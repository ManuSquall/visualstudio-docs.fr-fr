---
title: Outils de conteneur Visual Studio Docker Compose les paramètres de build
author: ghogen
description: Vue d’ensemble du processus de génération des outils de conteneur
ms.author: ghogen
ms.date: 08/12/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: c2f96bcc9df16b5de7d7f3ff485431352800d27e
ms.sourcegitcommit: 9801fc66a14c0f855b9ff601fb981a9e5321819e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74072725"
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

Vous pouvez ajouter le paramètre de propriété à un élément `PropertyGroup` existant ou, s’il n’en existe pas, créer un nouvel élément `PropertyGroup`.

## <a name="docker-compose-msbuild-properties"></a>Docker Compose les propriétés MSBuild

Le tableau suivant présente les propriétés MSBuild disponibles pour les projets Docker Compose.

| Nom de propriété | Emplacement | Description | Valeur par défaut  |
|---------------|----------|-------------|----------------|
|AdditionalComposeFiles|dcproj|Spécifie des fichiers compose supplémentaires dans une liste délimitée par des points-virgules à envoyer à docker-compose. exe pour toutes les commandes. Les chemins d’accès relatifs du fichier projet dockr-compose (dcproj) sont autorisés.|-|
|DockerComposeBaseFilePath|dcproj|Spécifie la première partie des noms de fichiers des fichiers de l’ancrage-compose, sans l’extension *. yml* . Exemple : <br>1. DockerComposeBaseFilePath = null/non défini : utilisez le chemin d’accès *de fichier de base dockr-compose*, et les fichiers sont nommés *docker-compose. yml* et *docker-compose. override. yml*<br>2. DockerComposeBaseFilePath = *mydockercompose*: les fichiers sont nommés *mydockercompose. yml* et *mydockercompose. override. yml*<br> 3. DockerComposeBaseFilePath = *.. \mydockercompose*: les fichiers sont situés un niveau. |docker-compose|
|DockerComposeBuildArguments|dcproj|Spécifie les paramètres supplémentaires à passer à la commande `docker-compose build`. Par exemple, `--parallel --pull`. |
|DockerComposeDownArguments|dcproj|Spécifie les paramètres supplémentaires à passer à la commande `docker-compose down`. Par exemple, `--timeout 500`.|-|  
|DockerComposeProjectPath|csproj ou vbproj|Chemin d’accès relatif au fichier de projet d’ancrage-compose (dcproj). Définissez cette propriété lors de la publication du projet de service pour rechercher les paramètres de génération d’image associés stockés dans le fichier docker-compose. yml.|-|
|DockerComposeUpArguments|dcproj|Spécifie les paramètres supplémentaires à passer à la commande `docker-compose up`. Par exemple, `--timeout 500`.|-|
|DockerLaunchAction| dcproj | Spécifie l’action de lancement à exécuter sur F5 ou CTRL + F5.  Les valeurs autorisées sont None, LaunchBrowser et LaunchWCFTestClient|aucune.|
|DockerLaunchBrowser| dcproj | Indique s’il faut lancer le navigateur. Ignoré si DockerLaunchAction est spécifié. | False |
|DockerServiceName| dcproj|Si DockerLaunchAction ou DockerLaunchBrowser sont spécifiés, DockerServiceName est le nom du service qui doit être lancé.  Utilisez cette propriété pour déterminer lequel des projets potentiellement référencés par un fichier d’ancrage-compose sera lancé.|-|
|DockerServiceUrl| dcproj | URL à utiliser lors du lancement du navigateur.  Les jetons de remplacement valides sont « {ServiceIPAddress} », « {ServicePort} » et « {Scheme} ».  Par exemple : {Scheme}://{ServiceIPAddress} : {ServicePort}|-|
|DockerTargetOS| dcproj | Le système d’exploitation cible utilisé lors de la génération de l’image de l’ancrage.|-|

## <a name="example"></a>Exemple

Si vous modifiez l’emplacement des fichiers compose de l’ancrage, en affectant à `DockerComposeBaseFilePath` un chemin d’accès relatif, vous devez également vous assurer que le contexte de génération est modifié de sorte qu’il fasse référence au dossier de solution. Par exemple, si votre fichier composer compose est un dossier appelé *DockerComposeFiles*, le fichier compose de l’ancrage doit définir le contexte de build sur « .. » ou «.. /..», en fonction de son emplacement par rapport au dossier de solution.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="15.0" Sdk="Microsoft.Docker.Sdk">
  <PropertyGroup Label="Globals">
    <ProjectVersion>2.1</ProjectVersion>
    <DockerTargetOS>Windows</DockerTargetOS>
    <ProjectGuid>154022c1-8014-4e9d-bd78-6ff46670ffa4</ProjectGuid>
    <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
    <DockerServiceUrl>{Scheme}://{ServiceIPAddress}{ServicePort}</DockerServiceUrl>
    <DockerServiceName>webapplication1</DockerServiceName>
    <DockerComposeBaseFilePath>DockerComposeFiles\mydockercompose</DockerComposeBaseFilePath>
    <AdditionalComposeFilePaths>AdditionalComposeFiles\myadditionalcompose.yml</AdditionalComposeFilePaths>
  </PropertyGroup>
  <ItemGroup>
    <None Include="DockerComposeFiles\mydockercompose.override.yml">
      <DependentUpon>DockerComposeFiles\mydockercompose.yml</DependentUpon>
    </None>
    <None Include="DockerComposeFiles\mydockercompose.yml" />
    <None Include=".dockerignore" />
  </ItemGroup>
</Project>
```

Le fichier *mydockercompose. yml* doit ressembler à ceci, avec le contexte de build défini sur le chemin d’accès relatif du dossier de solution (dans ce cas, `..`).

```yml
version: '3.4'

services:
  webapplication1:
    image: ${DOCKER_REGISTRY-}webapplication1
    build:
      context: ..
      dockerfile: WebApplication1\Dockerfile
```

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
