---
title: Vue d’ensemble de la génération et du débogage des outils de conteneur Visual Studio
author: ghogen
description: Vue d’ensemble du processus de génération et de débogage des outils de conteneur
ms.author: ghogen
ms.date: 11/20/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 6b96f23bc7bcd7e6d970025b23f89f572d07daf1
ms.sourcegitcommit: e825d1223579b44ee2deb62baf4de0153f99242a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2019
ms.locfileid: "74473993"
---
# <a name="build-and-debug-containerized-apps-using-visual-studio-or-the-command-line"></a>Générer et déboguer des applications en conteneur à l’aide de Visual Studio ou de la ligne de commande

Que vous génériez à partir de l’IDE de Visual Studio ou que vous configurez une génération à partir de la ligne de commande, vous devez savoir comment Visual Studio builds utilise fichier dockerfile pour générer vos projets.  Pour des raisons de performances, Visual Studio suit un processus spécial pour les applications en conteneur. Il est particulièrement important de comprendre comment Visual Studio génère vos projets lorsque vous personnalisez votre processus de génération en modifiant le fichier dockerfile.

Lorsque Visual Studio génère un projet qui n’utilise pas de conteneurs d’ancrage, il appelle MSBuild sur l’ordinateur local et génère les fichiers de sortie dans un dossier (généralement `bin`) dans votre dossier de solution local. Toutefois, pour un projet en conteneur, le processus de génération tient compte des instructions de fichier dockerfile pour la création de l’application en conteneur. Le fichier dockerfile utilisé par Visual Studio est divisé en plusieurs étapes. Ce processus s’appuie sur la fonctionnalité de *génération multiétape* de l’ancrage.

## <a name="multistage-build"></a>Génération multiétape

La fonctionnalité de génération multiétape permet de rendre le processus de création de conteneurs plus efficace et de réduire la taille des conteneurs en leur permettant de contenir uniquement les bits nécessaires à votre application au moment de l’exécution. La génération multiétape est utilisée pour les projets .NET Core, pas pour les projets .NET Framework.

La génération multiétape permet de créer des images de conteneur dans des étapes qui produisent des images intermédiaires. Par exemple, considérez un fichier dockerfile typique généré par Visual Studio : la première étape est `base`:

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
```

Les lignes du fichier dockerfile commencent par l’image nano Server de Microsoft Container Registry (mcr.microsoft.com) et créent une image intermédiaire `base` qui expose les ports 80 et 443, puis définit le répertoire de travail sur `/app`.

L’étape suivante est `build`, qui se présente comme suit :

```
FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY ["WebApplication43/WebApplication43.csproj", "WebApplication43/"]
RUN dotnet restore "WebApplication43/WebApplication43.csproj"
COPY . .
WORKDIR "/src/WebApplication43"
RUN dotnet build "WebApplication43.csproj" -c Release -o /app
```

Vous pouvez voir que l’étape `build` démarre à partir d’une image d’origine différente du Registre (`sdk` plutôt que `aspnet`), au lieu de se poursuivre à partir de la base.  L’image `sdk` possède tous les outils de génération et, pour cette raison, elle est beaucoup plus volumineuse que l’image ASPNET, qui contient uniquement des composants d’exécution. La raison de l’utilisation d’une image distincte devient évidente lorsque vous examinez le reste du fichier dockerfile :

```
FROM build AS publish
RUN dotnet publish "WebApplication43.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication43.dll"]
```

La dernière étape redémarre à partir de `base`, et comprend le `COPY --from=publish` pour copier la sortie publiée dans l’image finale. Ce processus permet à l’image finale d’être beaucoup plus petite, car elle n’a pas besoin d’inclure tous les outils de génération qui étaient dans l’image `sdk`.

## <a name="faster-builds-for-the-debug-configuration"></a>Builds plus rapides pour la configuration Debug

Il existe plusieurs optimisations que Visual Studio permet d’améliorer les performances du processus de génération pour les projets en conteneur. Le processus de génération pour les applications en conteneur n’est pas aussi simple que de suivre les étapes décrites dans fichier dockerfile. La génération dans un conteneur est beaucoup plus lente que la génération sur l’ordinateur local.  Ainsi, quand vous générez dans la configuration de **débogage** , Visual Studio génère en fait vos projets sur l’ordinateur local, puis partage le dossier de sortie vers le conteneur à l’aide du montage de volume. Une génération avec cette optimisation activée est appelée « génération en mode *rapide* ».

En mode **rapide** , Visual Studio appelle `docker build` avec un argument qui indique à dockr de générer uniquement l’étape de `base`.  Visual Studio gère le reste du processus sans tenir compte du contenu de l’fichier dockerfile. Ainsi, lorsque vous modifiez votre fichier dockerfile, par exemple pour personnaliser l’environnement de conteneur ou installer des dépendances supplémentaires, vous devez placer vos modifications dans la première étape.  Les étapes personnalisées placées dans les étapes `build`, `publish`ou `final` du fichier dockerfile ne seront pas exécutées.

Cette optimisation des performances se produit uniquement lorsque vous générez dans la configuration **Debug** . Dans la configuration **Release** , la génération se produit dans le conteneur comme spécifié dans fichier dockerfile.

Si vous souhaitez désactiver l’optimisation des performances et la génération comme le spécifie fichier dockerfile, définissez la propriété **ContainerDevelopmentMode** sur **Regular** dans le fichier projet comme suit :

```xml
<PropertyGroup>
   <ContainerDevelopmentMode>Regular</ContainerDevelopmentMode>
</PropertyGroup>
```

Pour restaurer l’optimisation des performances, supprimez la propriété du fichier projet.

## <a name="building-from-the-command-line"></a>Génération à partir de la ligne de commande

Vous pouvez utiliser `docker build` ou `MSBuild` pour générer à partir de la ligne de commande.

### <a name="docker-build"></a>version de l’arrimeur

Pour générer une solution en conteneur à partir de la ligne de commande, vous pouvez généralement utiliser la `docker build <context>` de commande pour chaque projet de la solution. Vous fournissez l’argument de *contexte de génération* . Le *contexte de génération* d’un fichier dockerfile est le dossier sur l’ordinateur local utilisé comme dossier de travail pour générer l’image. Par exemple, il s’agit du dossier à partir duquel vous copiez des fichiers lorsque vous copiez dans le conteneur.  Dans les projets .NET Core, utilisez le dossier qui contient le fichier solution (. sln).  Exprimée sous la forme d’un chemin d’accès relatif, cet argument correspond généralement à « .. » pour un fichier dockerfile dans un dossier de projet, et au fichier solution dans son dossier parent.  Pour les projets .NET Framework, le contexte de génération est le dossier du projet, et non le dossier de la solution.

```cmd
docker build -f Dockerfile ..
```

### <a name="msbuild"></a>MSBuild

Les fichiers dockerfile créés par Visual Studio pour les projets .NET Framework (et pour les projets .NET Core créés avec les versions de Visual Studio antérieures à Visual Studio 2017 Update 4) ne sont pas des fichiers dockerfile multiétapes.  Les étapes de ces fichiers dockerfile ne compilent pas votre code.  Au lieu de cela, quand Visual Studio génère un .NET Framework fichier dockerfile, il compile tout d’abord votre projet à l’aide de MSBuild.  Lorsque cela se produit, Visual Studio génère alors le fichier dockerfile, qui copie simplement la sortie de génération de MSBuild dans l’image de l’Ancreur résultant.  Étant donné que les étapes de compilation de votre code ne sont pas incluses dans fichier dockerfile, vous ne pouvez pas générer .NET Framework fichiers dockerfile à l’aide de `docker build` à partir de la ligne de commande. Vous devez utiliser MSBuild pour générer ces projets.

Pour générer une image pour un projet de conteneur d’ancrage unique, vous pouvez utiliser MSBuild avec l’option de commande `/t:ContainerBuild`. Exemple :

```cmd
MSBuild MyProject.csproj /t:ContainerBuild /p:Configuration=Release
```

Vous verrez une sortie similaire à ce que vous voyez dans la fenêtre **sortie** quand vous générez votre solution à partir de l’IDE de Visual Studio. Utilisez toujours `/p:Configuration=Release`, car dans les cas où Visual Studio utilise l’optimisation de génération multiétape, les résultats lors de la génération de la configuration **Debug** peuvent ne pas être les mêmes que prévu.

Si vous utilisez un projet Docker Compose, utilisez la commande pour créer des images :

```cmd
msbuild /p:SolutionPath=<solution-name>.sln /p:Configuration=Release docker-compose.dcproj
```

## <a name="project-warmup"></a>Préchauffage de projet

Il s’agit d’une séquence d’étapes qui se produisent lorsque le profil de l’ancrage est sélectionné pour un projet (autrement dit, quand un projet est chargé ou que la prise en charge de l’ancrage est ajoutée) afin d’améliorer les performances de l’exécution suivante (**F5** ou **CTRL**+**F5**). Cela peut être configuré sous **outils** > **options** > **outils de conteneur**. Voici les tâches qui s’exécutent en arrière-plan :

- Vérifiez que le Bureau de l’ordinateur de veille est installé et en cours d’exécution.
- Assurez-vous que l’ordinateur de bureau de l’arrimeur est défini sur le même système d’exploitation que le projet.
- Tirez les images dans la première étape du fichier dockerfile (l’étape `base` dans la plupart des fichiers dockerfile).  
- Générez le fichier dockerfile et démarrez le conteneur.

Le préchauffage ne se produit qu’en mode **rapide** . par conséquent, le conteneur en cours d’exécution aura le volume de dossier d’application monté et toute modification apportée à l’application ne doit pas invalider le conteneur. Cela améliore considérablement les performances de débogage et réduit le temps d’attente pour les tâches longues, telles que l’extraction d’images volumineuses.

## <a name="volume-mapping"></a>Mappage de volume

Pour que le débogage fonctionne dans des conteneurs, Visual Studio utilise le mappage de volume pour mapper le débogueur et les dossiers NuGet à partir de l’ordinateur hôte. Voici les volumes montés dans votre conteneur :

|||
|-|-|
| **Débogueur distant** | Contient les bits requis pour exécuter le débogueur dans le conteneur en fonction du type de projet. Cela est expliqué dans plus |détails dans la section [débogage](#debugging) .
| **Dossier d’application** | Contient le dossier du projet dans lequel se trouve le fichier dockerfile.|
| **Dossier source** | Contient le contexte de build qui est passé aux commandes de l’ancrage.|
| **Dossiers de packages NuGet** | Contient les packages NuGet et les dossiers de secours qui sont lus à partir du fichier *obj\{Project}. csproj. NuGet. g. props* dans le projet. |

Pour les applications Web ASP.NET Core, il peut y avoir deux dossiers supplémentaires pour le certificat SSL et les secrets de l’utilisateur, ce qui est expliqué plus en détail dans la section suivante.

## <a name="ssl-enabled-aspnet-core-apps"></a>Applications ASP.NET Core compatibles SSL

Les outils de conteneur de Visual Studio prennent en charge le débogage d’une application ASP.NET Core compatible SSL avec un certificat de développement, de la même façon que vous pouvez vous attendre à ce qu’elle fonctionne sans conteneurs. Pour ce faire, Visual Studio ajoute quelques étapes supplémentaires pour exporter le certificat et le mettre à la disposition du conteneur. Voici le flow :

1. Assurez-vous que le certificat de développement local est présent et approuvé sur l’ordinateur hôte par le biais de l’outil `dev-certs`.
2. Exportez le certificat vers%APPDATA%\ASP.NET\Https avec un mot de passe sécurisé stocké dans le magasin de secrets de l’utilisateur pour cette application particulière.
3. Monter en volume les répertoires suivants :

   - *%APPDATA%\Microsoft\UserSecrets*
   - *%APPDATA%\ASP.NET\Https*

ASP.NET Core recherche un certificat qui correspond au nom de l’assembly dans le dossier *https* , c’est pourquoi il est mappé au conteneur dans ce chemin d’accès. Le chemin d’accès et le mot de passe du certificat peuvent également être définis à l’aide de variables d’environnement (autrement dit, `ASPNETCORE_Kestrel__Certificates__Default__Path` et `ASPNETCORE_Kestrel__Certificates__Default__Password`) ou dans le fichier JSON de secrets d’utilisateur, par exemple :

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

Pour plus d’informations sur l’utilisation de SSL avec les applications de ASP.NET Core dans les conteneurs, consultez [hébergement d’images ASP.net core avec l’arrimeur sur https](https://docs.microsoft.com/aspnet/core/security/docker-https).

## <a name="debugging"></a>Débogage

 Quand vous démarrez le débogage (**F5**), un conteneur précédemment démarré est réutilisé, si possible. Si vous ne souhaitez pas réutiliser le conteneur précédent, vous pouvez utiliser des commandes de **régénération** ou de **nettoyage** dans Visual Studio pour forcer Visual Studio à utiliser un nouveau conteneur.

Le processus d’exécution du débogueur dépend du type de projet et du système d’exploitation du conteneur :

|||
|-|-|
| **Applications .NET Core (conteneurs Linux)**| Visual Studio télécharge `vsdbg` et le mappe au conteneur, puis il est appelé avec votre programme et les arguments (autrement dit, `dotnet webapp.dll`), puis le débogueur s’attache au processus. |
| **Applications .NET Core (conteneurs Windows)**| Visual Studio utilise `onecoremsvsmon` et le mappe au conteneur, l’exécute en tant que point d’entrée, puis Visual Studio s’y connecte et se connecte à votre programme. Cela est similaire à la façon dont vous configurez normalement le débogage distant sur un autre ordinateur ou ordinateur virtuel.|
| **Applications .NET Framework** | Visual Studio utilise `msvsmon` et le mappe au conteneur, l’exécute dans le cadre du point d’entrée auquel Visual Studio peut s’y connecter et se connecte à votre programme.|

Pour plus d’informations sur `vsdbg.exe`, consultez [débogage Offroad de .net Core sur Linux et OSX à partir de Visual Studio](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio).

## <a name="container-entry-point"></a>Point d’entrée de conteneur

Visual Studio utilise un point d’entrée de conteneur personnalisé en fonction du type de projet et du système d’exploitation de conteneur, Voici les différentes combinaisons :

|||
|-|-|
| **Conteneurs Linux** | Le point d’entrée est `tail -f /dev/null`, ce qui est une attente infinie de conserver le conteneur en cours d’exécution. Lorsque l’application est lancée par le biais du débogueur, c’est le débogueur qui est chargé d’exécuter l’application (autrement dit, `dotnet webapp.dll`). Si elle est lancée sans débogage, les outils exécutent une `docker exec -i {containerId} dotnet webapp.dll` pour exécuter l’application.|
| **Conteneurs Windows**| Le point d’entrée est semblable à `C:\remote_debugger\x64\msvsmon.exe /noauth /anyuser /silent /nostatus` qui exécute le débogueur. il écoute donc les connexions. Il en va de même pour le débogueur qui exécute l’application et une commande `docker exec` lorsqu’elle est lancée sans débogage. Pour les applications Web .NET Framework, le point d’entrée est légèrement différent lorsque `ServiceMonitor` est ajouté à la commande.|
  
> [!NOTE]
> Le point d’entrée de conteneur ne peut être modifié que dans des projets dockr-compose, et non dans des projets à conteneur unique.

## <a name="next-steps"></a>Étapes suivantes :

Découvrez comment personnaliser davantage vos builds en définissant des propriétés MSBuild supplémentaires dans vos fichiers projet. Consultez [propriétés MSBuild pour les projets de conteneur](container-msbuild-properties.md).

## <a name="see-also"></a>Voir aussi

[MSBuild](../msbuild/msbuild.md)
[fichier dockerfile sur Windows](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
les [conteneurs Linux sur Windows](/virtualization/windowscontainers/deploy-containers/linux-containers)
