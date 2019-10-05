---
title: Outils de conteneur Visual Studio Docker Compose les paramètres de build
author: ghogen
description: Vue d’ensemble du processus de génération des outils de conteneur
ms.author: ghogen
ms.date: 08/12/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 2178881c6ea0e597aef5e25074e3648162d3f6e9
ms.sourcegitcommit: 6ae0a289f1654dec63b412bfa22035511a2ef5ad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71950637"
---
# <a name="docker-compose-build-properties"></a>Docker Compose les propriétés de build

En plus des propriétés qui contrôlent des projets d’ancrage individuels, décrits dans les [Propriétés de génération des outils de conteneur](container-msbuild-properties.md), vous pouvez également personnaliser la façon dont Visual Studio génère vos projets docker compose en définissant les propriétés de docker compose que MSBuild utilise pour générer votre solution. Vous pouvez également contrôler la façon dont le débogueur Visual Studio exécute vos applications Docker Composees en définissant des étiquettes de fichier dans Docker Compose fichiers de configuration.

## <a name="how-to-set-the-msbuild-properties"></a>Comment définir les propriétés MSBuild

Pour définir la valeur d’une propriété, modifiez le fichier projet. Pour les propriétés de Docker Compose, ce fichier projet est celui avec une extension. dcproj, sauf indication contraire dans le tableau de la section suivante. Supposons, par exemple, que vous souhaitiez spécifier de lancer le navigateur lorsque vous démarrez le débogage. Vous pouvez définir la propriété `DockerLaunchAction` dans le fichier projet. dcproj comme suit.

```xml
<PropertyGroup>
   <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
</PropertyGroup>
```

Vous pouvez ajouter le paramètre de propriété à un élément `PropertyGroup` existant ou, si ce n’est pas le cas, créer un nouvel élément `PropertyGroup`.

## <a name="docker-compose-msbuild-properties"></a>Docker Compose les propriétés MSBuild

Le tableau suivant présente les propriétés MSBuild disponibles pour les projets Docker Compose.

| Nom de propriété | Location | Description | Valeur par défaut  |
|---------------|----------|-------------|----------------|
|DockerComposeBuildArguments|dcproj|Spécifie les paramètres supplémentaires à passer à la commande `docker-compose build`. Par exemple, `--parallel --pull`. |
|DockerComposeDownArguments|dcproj|Spécifie les paramètres supplémentaires à passer à la commande `docker-compose down`. Par exemple, `--timeout 500`.|-|  
|DockerComposeProjectPath|csproj ou vbproj|Chemin d’accès relatif au fichier de projet d’ancrage-compose (dcproj). Définissez cette propriété lors de la publication du projet de service pour rechercher les paramètres de génération d’image associés stockés dans le fichier docker-compose. yml.|-|
|DockerComposeUpArguments|dcproj|Spécifie les paramètres supplémentaires à passer à la commande `docker-compose up`. Par exemple, `--timeout 500`.|-|
|DockerLaunchAction| dcproj | Spécifie l’action de lancement à exécuter sur F5 ou CTRL + F5.  Les valeurs autorisées sont None, LaunchBrowser et LaunchWCFTestClient|Aucun.|
|DockerLaunchBrowser| dcproj | Indique s’il faut lancer le navigateur. Ignoré si DockerLaunchAction est spécifié. | False |
|DockerServiceName| dcproj|Si DockerLaunchAction ou DockerLaunchBrowser sont spécifiés, DockerServiceName est le nom du service qui doit être lancé.  Utilisez cette propriété pour déterminer lequel des projets potentiellement référencés par un fichier d’ancrage-compose sera lancé.|-|
|DockerServiceUrl| dcproj | URL à utiliser lors du lancement du navigateur.  Les jetons de remplacement valides sont « {ServiceIPAddress} », « {ServicePort} » et « {Scheme} ».  Par exemple : {Scheme}://{ServiceIPAddress} : {ServicePort}|-|
|DockerTargetOS| dcproj | Le système d’exploitation cible utilisé lors de la génération de l’image de l’ancrage.|-|

> [!NOTE]
> DockerComposeBuildArguments, DockerComposeDownArguments et DockerComposeUpArguments sont nouveaux dans Visual Studio 2019 version 16,3.

## <a name="docker-compose-file-labels"></a>Étiquettes de fichier Docker Compose

Vous pouvez également remplacer certains paramètres en plaçant un fichier nommé *docker-compose. vs. Debug. yml* (pour la configuration **Debug** ) ou *docker-compose. vs. Release. yml* (pour la configuration **Release** ) dans le même répertoire que votre  *fichier docker-compose. yml* .  Dans ce fichier, vous pouvez spécifier les paramètres comme suit :

```yml
services:
  webapplication1:
    labels:
      com.microsoft.visualstudio.debuggee.workingdirectory: "C:\\my_app_folder"
```

Utilisez des guillemets doubles autour des valeurs, comme dans l’exemple précédent, et utilisez la barre oblique inverse comme caractère d’échappement pour les barres obliques inverses dans les chemins d’accès.

|Nom d'étiquette|Description|
|----------|-----------|
|com. Microsoft. VisualStudio. Debugger. arguments|Arguments passés au programme lors du démarrage du débogage. Pour les applications .NET Core, ces arguments sont généralement des chemins de recherche supplémentaires pour les packages NuGet, suivis du chemin d’accès à l’assembly de sortie du projet.|
|com. Microsoft. VisualStudio. Debugger. killprogram|Cette commande permet d’arrêter le programme débogué qui s’exécute dans le conteneur (si nécessaire).|
|com. Microsoft. VisualStudio. Debugger. Program|Le programme est lancé au démarrage du débogage. Pour les applications .NET Core, ce paramètre est généralement **dotnet**.|
|com. Microsoft. VisualStudio. Debugger. WorkingDirectory|Répertoire utilisé comme répertoire de démarrage lors du démarrage du débogage. Ce paramètre est généralement */app* pour les conteneurs Linux ou *C:\app* pour les conteneurs Windows.|

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les propriétés MSBuild en général, consultez [propriétés MSBuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Voir aussi

[Propriétés de build des outils de conteneur](container-msbuild-properties.md)

[Paramètres de lancement des outils de conteneur](container-launch-settings.md)

[Propriétés réservées et connues de MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
