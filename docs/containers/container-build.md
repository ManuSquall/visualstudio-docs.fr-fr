---
title: Visual Studio Container Tools construire et déboiser aperçu
author: ghogen
description: Aperçu du processus de construction et de débogage des outils de conteneurs
ms.author: ghogen
ms.date: 11/20/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: d91dd01879ac3bb62b981109463f6762046382ef
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027260"
---
# <a name="how-visual-studio-builds-containerized-apps"></a>Comment Visual Studio génère des applications conteneurisées

Que vous construisiez à partir de l’IDE Visual Studio ou que vous installiez une gamme de commandes, vous devez savoir comment Visual Studio utilise le Dockerfile pour construire vos projets.  Pour des raisons de performance, Visual Studio suit un processus spécial pour les applications conteneurisées. Comprendre comment Visual Studio construit vos projets est particulièrement important lorsque vous personnalisez votre processus de construction en modifiant le Dockerfile.

Lorsque Visual Studio construit un projet qui n’utilise pas de conteneurs Docker, il invoque MSBuild `bin`sur la machine locale et génère les fichiers de sortie dans un dossier (généralement) sous votre dossier de solution local. Pour un projet conteneurisé, cependant, le processus de construction tient compte des instructions du Dockerfile pour la construction de l’application conteneurisée. Le Dockerfile celui Visual Studio utilise est divisé en plusieurs étapes. Ce processus repose sur la fonction de *construction multistâmaux* de Docker.

## <a name="multistage-build"></a>Construction multitâmarure

La fonction de construction multistâches contribue à rendre le processus de construction des conteneurs plus efficace, et rend les conteneurs plus petits en leur permettant de contenir uniquement les bits dont votre application a besoin au moment de l’exécution. La construction multistâmeuse est utilisée pour les projets de base .NET, et non pour les projets cadre .NET.

La construction multistâmable permet de créer des images de conteneurs par étapes qui produisent des images intermédiaires. À titre d’exemple, considérez un Dockerfile typique `base`généré par Visual Studio - la première étape est :

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
```

Les lignes dans le Dockerfile commencent avec l’image Debian de Microsoft Container `base` Registry (mcr.microsoft.com) et de créer une image intermédiaire qui `/app`expose les ports 80 et 443, et définit l’annuaire de travail à .

L’étape `build`suivante est , qui apparaît comme suit:

```
FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY ["WebApplication43/WebApplication43.csproj", "WebApplication43/"]
RUN dotnet restore "WebApplication43/WebApplication43.csproj"
COPY . .
WORKDIR "/src/WebApplication43"
RUN dotnet build "WebApplication43.csproj" -c Release -o /app
```

Vous pouvez voir `build` que la scène commence à`sdk` partir `aspnet`d’une image originale différente du registre ( plutôt que ), plutôt que de continuer à partir de la base.  L’image `sdk` a tous les outils de construction, et pour cette raison, il est beaucoup plus grand que l’image aspnet, qui ne contient que des composants de temps d’exécution. La raison de l’utilisation d’une image séparée devient claire lorsque vous regardez le reste du Dockerfile:

```
FROM build AS publish
RUN dotnet publish "WebApplication43.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication43.dll"]
```

La dernière étape `base`recommence à `COPY --from=publish` partir de , et comprend le copier la sortie publiée à l’image finale. Ce processus permet à l’image finale d’être beaucoup plus petite, car elle n’a `sdk` pas besoin d’inclure tous les outils de construction qui étaient dans l’image.

## <a name="building-from-the-command-line"></a>Bâtiment à partir de la ligne de commandement

Si vous souhaitez construire en dehors de `docker build` `MSBuild` Visual Studio, vous pouvez utiliser ou construire à partir de la ligne de commande.

### <a name="docker-build"></a>docker build

Pour construire une solution conteneurisée à partir de `docker build <context>` la ligne de commande, vous pouvez généralement utiliser la commande pour chaque projet dans la solution. Vous fournissez l’argument du *contexte de construction.* Le *contexte de construction* d’un Dockerfile est le dossier de la machine locale qui est utilisé comme dossier de travail pour générer l’image. Par exemple, c’est le dossier que vous copiez des fichiers à partir du moment où vous copiez au conteneur.  Dans les projets .NET Core, utilisez le dossier qui contient le fichier de solution (.sln).  Exprimé comme un chemin relatif, cet argument est généralement ".." pour un Dockerfile dans un dossier de projet, et le fichier de solution dans son dossier parent.  Pour les projets cadre .NET, le contexte de construction est le dossier de projet, pas le dossier de solution.

```cmd
docker build -f Dockerfile ..
```

### <a name="msbuild"></a>MSBuild

Dockerfiles créé par Visual Studio pour des projets cadre .NET (et pour les projets .NET Core créés avec des versions de Visual Studio avant Visual Studio 2017 Update 4) ne sont pas des Dockerfiles multi-scènes.  Les étapes de ces Dockerfiles ne compilent pas votre code.  Au lieu de cela, lorsque Visual Studio construit un .NET Framework Dockerfile, il compile d’abord votre projet à l’aide de MSBuild.  Lorsque cela réussit, Visual Studio construit ensuite le Dockerfile, qui copie simplement la sortie de construction de MSBuild dans l’image Docker résultant.  Parce que les étapes pour compiler votre code ne sont pas incluses dans le `docker build` Dockerfile, vous ne pouvez pas construire .NET Framework Dockerfiles à partir de la ligne de commande. Vous devriez utiliser MSBuild pour construire ces projets.

Pour construire une image pour un seul projet de `/t:ContainerBuild` conteneur docker, vous pouvez utiliser MSBuild avec l’option de commande. Par exemple :

```cmd
MSBuild MyProject.csproj /t:ContainerBuild /p:Configuration=Release
```

Vous verrez des sorties similaires à ce que vous voyez dans la fenêtre **output** lorsque vous construisez votre solution à partir de l’IDE Visual Studio. Toujours `/p:Configuration=Release`utiliser , puisque dans les cas où Visual Studio utilise l’optimisation de construction multistâles, les résultats lors de la construction de la configuration **Debug** pourrait ne pas être comme prévu. Voir [Debugging](#debugging).

Si vous utilisez un projet Docker Compose, utilisez cette commande pour construire des images :

```cmd
msbuild /p:SolutionPath=<solution-name>.sln /p:Configuration=Release docker-compose.dcproj
```

## <a name="project-warmup"></a>Échauffement du projet

*L’échauffement* du projet fait référence à une série d’étapes qui se produisent lorsque le profil Docker est sélectionné pour un projet (c’est-à-dire lorsqu’un projet est chargé ou qu’un support Docker est ajouté) afin d’améliorer les performances des courses suivantes (**F5** ou **Ctrl**+**F5**). Ceci est configurable dans **Tools** > **Options** > **Container Tools**. Voici les tâches qui s’exécutent en arrière-plan :

- Vérifiez que Docker Desktop est installé et en cours d’exécution.
- Assurez-vous que Docker Desktop est réglé sur le même système d’exploitation que le projet.
- Tirez les images dans la première étape `base` du Dockerfile (la scène dans la plupart des Dockerfiles).  
- Construisez le Dockerfile et démarrez le conteneur.

L’échauffement ne se fera **qu’en** mode rapide, de sorte que le conteneur en cours d’exécution aura le volume de l’application monté. Cela signifie que toute modification de l’application n’invalide pas le conteneur. Cela améliore donc considérablement les performances de débogage et diminue le temps d’attente pour les tâches de longue durée telles que la traction de grandes images.

## <a name="volume-mapping"></a>Cartographie du volume

Pour que le débogage fonctionne dans des conteneurs, Visual Studio utilise la cartographie du volume pour cartographier les dossiers de débogage et de NuGet de la machine hôte. La cartographie du volume est décrite dans la documentation Docker [ici](https://docs.docker.com/storage/volumes/). Voici les volumes qui sont montés dans votre conteneur :

|||
|-|-|
| **Débbugger à distance** | Contient les bits nécessaires pour faire fonctionner le débbuggeur dans le conteneur en fonction du type de projet. Cela s’explique dans plus de |détail dans la section [Debugging.](#debugging)
| **Dossier d’application** | Contient le dossier de projet où se trouve le Dockerfile.|
| **Dossier source** | Contient le contexte de construction qui est passé aux commandes Docker.|
| **Dossiers de paquets NuGet** | Contient les paquets NuGet et les dossiers de repli qui sont lus à partir du *fichier obj\{project.csproj.nuget.g.props* dans le projet. |

Pour ASP.NET applications Web de base, il peut y avoir deux dossiers supplémentaires pour le certificat SSL et les secrets d’utilisateur, qui est expliqué plus en détail dans la section suivante.

## <a name="ssl-enabled-aspnet-core-apps"></a>Applications de base ASP.NET activées par SSL

Les outils de conteneurs dans Visual Studio support de déboguer une application de base de ASP.NET SSL avec un certificat de dev, de la même façon que vous vous attendez à ce qu’il fonctionne sans conteneurs. Pour ce faire, Visual Studio ajoute quelques étapes de plus pour exporter le certificat et le mettre à la disposition du conteneur. Voici le flux que Visual Studio gère pour vous lors de la débogage dans le conteneur:

1. Assure que le certificat de développement local est `dev-certs` présent et fait confiance à la machine hôte à travers l’outil.
2. Exporte le certificat à %APPDATA%-ASP.NET-Https avec un mot de passe sécurisé qui est stocké dans le magasin de secrets d’utilisateur pour cette application particulière.
3. Volume-monte les répertoires suivants:

   - *%APPDATA%-Microsoft-UserSecrets*
   - *%APPDATA%-ASP.NET-Https*

ASP.NET Core cherche un certificat qui correspond au nom de l’assemblage sous le dossier *Https,* c’est pourquoi il est cartographié sur le conteneur dans ce sens. Le chemin de certificat et mot de passe peuvent `ASPNETCORE_Kestrel__Certificates__Default__Path` `ASPNETCORE_Kestrel__Certificates__Default__Password`être définis alternativement à l’aide de variables de l’environnement (c’est-à-dire et) ou dans le fichier json secrets d’utilisateur, par exemple :

```json
{
  "Kestrel": {
    "Certificates": {
      "Default": {
        "Path": "c:\\app\\mycert.pfx",
        "Password": "strongpassword"
      }
    }
  }
}
```

Si votre configuration prend en charge les constructions conteneurisées et non conteneurisées, vous devez utiliser les variables de l’environnement, car les chemins sont spécifiques à l’environnement des conteneurs.

Pour plus d’informations sur l’utilisation de SSL avec ASP.NET applications Core dans des conteneurs, voir [Hosting ASP.NET Images Core avec Docker sur HTTPS](/aspnet/core/security/docker-https)).

## <a name="debugging"></a>Débogage

Lors de la construction dans la configuration **Debug,** il ya plusieurs optimisations que Visual Studio fait qui aident à la performance du processus de construction pour les projets conteneurisés. Le processus de construction d’applications conteneurisées n’est pas aussi simple que de simplement suivre les étapes décrites dans le Dockerfile. Construire dans un conteneur est beaucoup plus lent que de construire sur la machine locale.  Ainsi, lorsque vous construisez dans la configuration **Debug,** Visual Studio construit réellement vos projets sur la machine locale, puis partage le dossier de sortie au conteneur en utilisant le montage de volume. Une version avec cette optimisation activée est appelée une version en mode *rapide.*

En mode **Fast,** `docker build` Visual Studio appelle avec un `base` argument qui dit Docker de construire seulement la scène.  Visual Studio gère le reste du processus sans tenir compte du contenu du Dockerfile. Ainsi, lorsque vous modifiez votre Dockerfile, par exemple pour personnaliser l’environnement du conteneur ou installer des dépendances supplémentaires, vous devez mettre vos modifications dans la première étape.  Toutes les étapes personnalisées placées `build` `publish`dans `final` le Dockerfile, ou les étapes ne seront pas exécutées.

Cette optimisation des performances ne se produit que lorsque vous construisez dans la configuration **Debug.** Dans la configuration **De libération,** la construction se produit dans le conteneur tel que spécifié dans le Dockerfile.

Si vous souhaitez désactiver l’optimisation des performances et construire au fur et à mesure que le Dockerfile le précise, définissez la propriété **ContainerDevelopmentMode** à **Regular** dans le dossier du projet comme suit :

```xml
<PropertyGroup>
   <ContainerDevelopmentMode>Regular</ContainerDevelopmentMode>
</PropertyGroup>
```

Pour rétablir l’optimisation des performances, retirez la propriété du fichier du projet.

 Lorsque vous commencez à débogage (**F5**), un conteneur précédemment commencé est réutilisé, si possible. Si vous ne souhaitez pas réutiliser le conteneur précédent, vous pouvez utiliser des commandes **Rebuild** ou **Clean** dans Visual Studio pour forcer Visual Studio à utiliser un nouveau conteneur.

Le processus d’exécution du débbuggeur dépend du type de système d’exploitation de projets et de conteneurs :

|||
|-|-|
| **.NET Applications de base (conteneurs Linux)**| Visual Studio `vsdbg` le télécharge et le cartographie au conteneur, puis il est `dotnet webapp.dll`appelé avec votre programme et les arguments (c’est-à-dire, ), puis débbugger se fixe au processus. |
| **.NET Applications de base (conteneurs Windows)**| Visual Studio `onecoremsvsmon` l’utilise et le cartographie au conteneur, l’exécute comme point d’entrée, puis Visual Studio se connecte à lui et se fixe à votre programme. Ceci est similaire à la façon dont vous seriez normalement configurer débugging à distance sur un autre ordinateur ou une machine virtuelle.|
| **.NET Framework apps** | Visual Studio `msvsmon` l’utilise et le cartographie au conteneur, l’exécute dans le cadre du point d’entrée où Visual Studio peut se connecter à lui, et se fixe à votre programme.|

Pour plus `vsdbg.exe`d’informations sur , voir [Offroad débogage de .NET Core sur Linux et OSX de Visual Studio](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio).

## <a name="container-entry-point"></a>Point d’entrée de conteneur

Visual Studio utilise un point d’entrée de conteneur personnalisé en fonction du type de projet et du système d’exploitation du conteneur, voici les différentes combinaisons :

|||
|-|-|
| **Conteneurs Linux** | Le point `tail -f /dev/null`d’entrée est, qui est une attente infinie pour garder le conteneur en cours d’exécution. Lorsque l’application est lancée par le débbugger, c’est le débbuggeur `dotnet webapp.dll`qui est responsable d’exécuter l’application (c’est-à-dire, ). Si elle est lancée sans débogage, l’outillage fonctionne `docker exec -i {containerId} dotnet webapp.dll` un pour exécuter l’application.|
| **Conteneurs Windows**| Le point d’entrée est quelque chose comme `C:\remote_debugger\x64\msvsmon.exe /noauth /anyuser /silent /nostatus` qui fonctionne le débbugger, il est donc à l’écoute pour les connexions. Il en va de même pour le `docker exec` débogage exécute l’application, et une commande lorsqu’elle est lancée sans débogage. Pour les applications Web .NET Framework, `ServiceMonitor` le point d’entrée est légèrement différent où est ajouté à la commande.|

Le point d’entrée des conteneurs ne peut être modifié que dans les projets docker-compose, et non dans les projets à conteneur unique.

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment personnaliser davantage vos builds en définissant d’autres propriétés MSBuild dans vos fichiers de projet. Voir [les propriétés MSBuild pour les projets de conteneurs](container-msbuild-properties.md).

## <a name="see-also"></a>Voir aussi

[MSBuild](../msbuild/msbuild.md)
[Dockerfile sur](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
[les conteneurs](/virtualization/windowscontainers/deploy-containers/linux-containers) Windows Linux sur Windows
