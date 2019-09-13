---
title: Vue d’ensemble de la génération des outils de conteneur Visual Studio
author: ghogen
description: Vue d’ensemble du processus de génération des outils de conteneur
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 9f2da112bfeebe4e0bce976736eee5696d888105
ms.sourcegitcommit: c7b9ab1bc19d74b635c19b1937e92c590dafd736
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2019
ms.locfileid: "70312025"
---
# <a name="building-containerized-apps-using-visual-studio-or-the-command-line"></a>Génération d’applications en conteneur à l’aide de Visual Studio ou de la ligne de commande

Que vous génériez à partir de l’IDE de Visual Studio ou que vous configurez une génération à partir de la ligne de commande, vous devez savoir comment Visual Studio builds utilise fichier dockerfile pour générer vos projets.  Pour des raisons de performances, Visual Studio suit un processus spécial pour les applications en conteneur. Il est particulièrement important de comprendre comment Visual Studio génère vos projets lorsque vous personnalisez votre processus de génération en modifiant le fichier dockerfile.

Lorsque Visual Studio génère un projet qui n’utilise pas de conteneurs d’ancrage, il appelle MSBuild sur l’ordinateur local et génère les fichiers de sortie dans un dossier `bin`(en général) dans votre dossier de solution local. Toutefois, pour un projet en conteneur, le processus de génération tient compte des instructions de fichier dockerfile pour la création de l’application en conteneur. Le fichier dockerfile utilisé par Visual Studio est divisé en plusieurs étapes. Ce processus s’appuie sur la fonctionnalité de *génération multiétape* de l’ancrage.

## <a name="multistage-build"></a>Génération multiétape

La fonctionnalité de génération multiétape permet de rendre le processus de création de conteneurs plus efficace et de réduire la taille des conteneurs en leur permettant de contenir uniquement les bits nécessaires à votre application au moment de l’exécution. La génération multiétape est utilisée pour les projets .NET Core, pas pour les projets .NET Framework.

La génération multiétape permet de créer des images de conteneur dans des étapes qui produisent des images intermédiaires. Par exemple, considérez un fichier dockerfile typique généré par Visual Studio : la première étape est `base`la suivante :

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
```

Les lignes de la fichier dockerfile commencent par l’image de serveur de Microsoft Container Registry (MCR.Microsoft.com) et créent une image `base` intermédiaire qui expose les ports 80 et 443, puis définit le répertoire de travail sur. `/app`

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

Vous pouvez voir que l' `build` étape démarre à partir d’une image d’origine différente du`sdk` Registre ( `aspnet`plutôt que), plutôt que de continuer à partir de la base.  L' `sdk` image contient tous les outils de génération et, pour cette raison, elle est beaucoup plus volumineuse que l’image ASPNET, qui contient uniquement des composants d’exécution. La raison de l’utilisation d’une image distincte devient évidente lorsque vous examinez le reste du fichier dockerfile :

```
FROM build AS publish
RUN dotnet publish "WebApplication43.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication43.dll"]
```

La dernière étape redémarre à `base`partir de et comprend `COPY --from=publish` le pour copier la sortie publiée dans l’image finale. Ce processus permet à l’image finale d’être beaucoup plus petite, car elle n’a pas besoin d’inclure tous les outils de génération qui étaient dans l' `sdk` image.

## <a name="faster-builds-for-the-debug-configuration"></a>Builds plus rapides pour la configuration Debug

Il existe plusieurs optimisations que Visual Studio permet d’améliorer les performances du processus de génération pour les projets en conteneur. Lorsque vous démarrez le débogage (F5), une image précédemment générée est réutilisée, si possible. Si vous ne souhaitez pas réutiliser le conteneur précédent, vous pouvez utiliser des commandes de **régénération** ou de **nettoyage** dans Visual Studio pour forcer Visual Studio à utiliser un nouveau conteneur.

En outre, pour améliorer les performances, le processus de génération des applications en conteneur n’est pas aussi simple que de suivre les étapes décrites dans le fichier dockerfile. La génération dans un conteneur est beaucoup plus lente que la génération sur l’ordinateur local.  Ainsi, quand vous générez dans la configuration de **débogage** , Visual Studio génère en fait vos projets sur l’ordinateur local, puis partage le dossier de sortie vers le conteneur à l’aide du montage de volume. Une génération avec cette optimisation activée est appelée « génération en mode *rapide* ».

En mode **rapide** , Visual Studio appelle `docker build` avec un argument qui indique à dockr de générer uniquement `base` l’étape.  Visual Studio gère le reste du processus sans tenir compte du contenu de l’fichier dockerfile. Ainsi, lorsque vous modifiez votre fichier dockerfile, par exemple pour personnaliser l’environnement de conteneur ou installer des dépendances supplémentaires, vous devez placer vos modifications dans la première étape.  Toutes les étapes personnalisées placées dans `build`les `publish`étapes, `final` ou de fichier dockerfile ne seront pas exécutées.

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

Pour générer une solution en conteneur à partir de la ligne de commande, vous pouvez généralement `docker build <context>` utiliser la commande pour chaque projet de la solution. Vous fournissez l’argument de *contexte de génération* . Le *contexte de génération* d’un fichier dockerfile est le dossier sur l’ordinateur local utilisé comme dossier de travail pour générer l’image. Par exemple, il s’agit du dossier à partir duquel vous copiez des fichiers lorsque vous copiez dans le conteneur.  Dans les projets .NET Core, utilisez le dossier qui contient le fichier solution (. sln).  Exprimée sous la forme d’un chemin d’accès relatif, cet argument correspond généralement à « .. » pour un fichier dockerfile dans un dossier de projet, et au fichier solution dans son dossier parent.  Pour les projets .NET Framework, le contexte de génération est le dossier du projet, et non le dossier de la solution.

```cmd
docker build -f Dockerfile ..
```

### <a name="msbuild"></a>MSBuild

Les fichiers dockerfile créés par Visual Studio pour les projets .NET Framework (et pour les projets .NET Core créés avec les versions de Visual Studio antérieures à Visual Studio 2017 Update 4) ne sont pas des fichiers dockerfile multiétapes.  Les étapes de ces fichiers dockerfile ne compilent pas votre code.  Au lieu de cela, quand Visual Studio génère un .NET Framework fichier dockerfile, il compile tout d’abord votre projet à l’aide de MSBuild.  Lorsque cela se produit, Visual Studio génère alors le fichier dockerfile, qui copie simplement la sortie de génération de MSBuild dans l’image de l’Ancreur résultant.  Étant donné que les étapes de compilation de votre code ne sont pas incluses dans fichier dockerfile, vous ne `docker build` pouvez pas générer .NET Framework fichiers dockerfile à l’aide de à partir de la ligne de commande. Vous devez utiliser MSBuild pour générer ces projets.

Pour générer une image pour un projet de conteneur d’ancrage unique, vous pouvez utiliser `/t:ContainerBuild` MSBuild avec l’option de commande. Par exemple :

```cmd
MSBuild MyProject.csproj /t:ContainerBuild /p:Configuration=Release
```

Vous verrez une sortie similaire à ce que vous voyez dans la fenêtre **sortie** quand vous générez votre solution à partir de l’IDE de Visual Studio. Utilisez `/p:Configuration=Release`toujours, puisque dans les cas où Visual Studio utilise l’optimisation de génération multiétape, les résultats lors de la génération de la configuration de **débogage** peuvent ne pas être les mêmes que prévu.

Si vous utilisez un projet Docker Compose, utilisez la commande pour créer des images :

```cmd
msbuild /p:SolutionPath=<solution-name>.sln /p:Configuration=Release docker-compose.dcproj
```

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment personnaliser davantage vos builds en définissant des propriétés MSBuild supplémentaires dans vos fichiers projet. Consultez [propriétés MSBuild pour les projets de conteneur](container-msbuild-properties.md).

## <a name="see-also"></a>Voir aussi

[MSBuild](../msbuild/msbuild.md)
[dockerfile sur Windows](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
[Linux conteneurs sur Windows](/virtualization/windowscontainers/deploy-containers/linux-containers)
