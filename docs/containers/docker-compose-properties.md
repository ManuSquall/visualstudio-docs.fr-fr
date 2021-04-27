---
title: Docker Compose les paramètres de build
author: ghogen
description: Découvrez comment modifier les propriétés de build Docker Compose pour personnaliser la façon dont Visual Studio génère et exécute une application Docker Compose.
ms.custom: SEO-VS-2020
ms.author: ghogen
ms.date: 04/06/2021
ms.technology: vs-azure
ms.topic: reference
ms.openlocfilehash: ed4b2a0dc1dc7a0520bf8e83ab1968a3815196e0
ms.sourcegitcommit: e12d6cdaeb37564f05361965db2ec8ad0d4f21ad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2021
ms.locfileid: "108025863"
---
# <a name="docker-compose-build-properties"></a>Docker Compose les propriétés de build

En plus des propriétés qui contrôlent des projets d’ancrage individuels, décrits dans les [Propriétés de génération des outils de conteneur](container-msbuild-properties.md), vous pouvez également personnaliser la façon dont Visual Studio génère vos projets docker compose en définissant les propriétés de docker compose utilisées par MSBuild pour générer votre solution. Vous pouvez également contrôler la façon dont le débogueur Visual Studio exécute vos applications Docker Composees en définissant des étiquettes de fichier dans Docker Compose fichiers de configuration.

## <a name="how-to-set-the-msbuild-properties"></a>Comment définir les propriétés MSBuild

Pour définir la valeur d’une propriété, modifiez le fichier projet. Pour les propriétés de Docker Compose, ce fichier projet est celui avec une extension. dcproj, sauf indication contraire dans le tableau de la section suivante. Supposons, par exemple, que vous souhaitiez spécifier de lancer le navigateur lorsque vous démarrez le débogage. Vous pouvez définir la `DockerLaunchAction` propriété dans le fichier projet. dcproj comme suit.

```xml
<PropertyGroup>
   <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
</PropertyGroup>
```

Vous pouvez ajouter le paramètre de propriété à un `PropertyGroup` élément existant, ou s’il n’y en a pas, créer un nouvel `PropertyGroup` élément.

## <a name="docker-compose-msbuild-properties"></a>Propriétés MSBuild Docker Compose

Le tableau suivant présente les propriétés MSBuild disponibles pour les projets Docker Compose.

| Nom de la propriété | Emplacement | Description | Valeur par défaut  |
|---------------|----------|-------------|----------------|
|AdditionalComposeFilePaths|dcproj|Spécifie des fichiers compose supplémentaires dans une liste délimitée par des points-virgules à envoyer à docker-compose.exe pour toutes les commandes. Les chemins d’accès relatifs du fichier projet dockr-compose (dcproj) sont autorisés.|-|
|DockerComposeBaseFilePath|dcproj|Spécifie la première partie des noms de fichiers des fichiers de l’ancrage-compose, sans l’extension *. yml* . Par exemple : <br>1. DockerComposeBaseFilePath = null/non défini : utilisez le chemin d’accès *de fichier de base dockr-compose*, et les fichiers sont nommés *docker-compose. yml* et *docker-compose. override. yml*.<br>2. DockerComposeBaseFilePath = *mydockercompose*: les fichiers sont nommés *mydockercompose. yml* et *mydockercompose. override. yml*.<br> 3. DockerComposeBaseFilePath = *.. \mydockercompose*: les fichiers sont situés un niveau. |docker-compose|
|DockerComposeBuildArguments|dcproj|Spécifie les paramètres supplémentaires à passer à la `docker-compose build` commande. Par exemple : `--parallel --pull`. |
|DockerComposeDownArguments|dcproj|Spécifie les paramètres supplémentaires à passer à la `docker-compose down` commande. Par exemple : `--timeout 500`.|-|  
|DockerComposeProjectName| dcproj | S’il est spécifié, remplace le nom de projet d’un projet dockr-compose. | « dockercompose » + hachage généré automatiquement |
|DockerComposeProjectPath|csproj ou vbproj|Chemin d’accès relatif au fichier de projet d’ancrage-compose (dcproj). Définissez cette propriété lors de la publication du projet de service pour rechercher les paramètres de génération d’image associés stockés dans le fichier docker-compose. yml.|-|
|DockerComposeProjectsToIgnore|dcproj| Spécifie les projets qui doivent être ignorés par les outils de l’ancrage-compose pendant le débogage. Cette propriété peut être utilisée pour n’importe quel projet. Les chemins d’accès aux fichiers peuvent être spécifiés de deux façons : <br> 1. relatif à dcproj. Par exemple : `<DockerComposeProjectsToIgnore>path\to\AngularProject1.csproj</DockerComposeProjectsToIgnore>`. <br> 2. chemins d’accès absolus.<br> **Remarque**: les chemins d’accès doivent être séparés par le caractère délimiteur `;` .|-|
|DockerComposeUpArguments|dcproj|Spécifie les paramètres supplémentaires à passer à la `docker-compose up` commande. Par exemple : `--timeout 500`.|-|
|DockerDevelopmentMode| dcproj | Contrôle si le projet utilisateur est généré dans le conteneur. Valeurs autorisées de contrôle **rapide** ou **régulier** des [étapes qui sont créées](https://aka.ms/containerfastmode) dans un fichier dockerfile. La configuration de débogage est le mode rapide par défaut et le mode normal dans le cas contraire. | Rapide |
|DockerLaunchAction| dcproj | Spécifie l’action de lancement à exécuter sur F5 ou CTRL + F5.  Les valeurs autorisées sont None, LaunchBrowser et LaunchWCFTestClient. | None |
|DockerLaunchBrowser| dcproj | Indique s’il faut lancer le navigateur. Ignoré si DockerLaunchAction est spécifié. | Faux |
|DockerServiceName| dcproj| Si DockerLaunchAction ou DockerLaunchBrowser sont spécifiés, DockerServiceName spécifie le service auquel il est fait référence dans le fichier d’ancrage-compose.|-|
|DockerServiceUrl| dcproj | URL à utiliser lors du lancement du navigateur.  Les jetons de remplacement valides sont « {ServiceIPAddress} », « {ServicePort} » et « {Scheme} ».  Par exemple : {Scheme}://{ServiceIPAddress} : {ServicePort}|-|
|DockerTargetOS| dcproj | Le système d’exploitation cible utilisé lors de la génération de l’image de l’ancrage.|-|

## <a name="example"></a>Exemple

Si vous modifiez l’emplacement des fichiers compose de l’ancrage, en définissant `DockerComposeBaseFilePath` sur un chemin d’accès relatif, vous devez également vous assurer que le contexte de génération est modifié de sorte qu’il fasse référence au dossier de solution. Par exemple, si votre fichier composer compose est un dossier appelé *DockerComposeFiles*, le fichier compose de l’ancrage doit définir le contexte de build sur « .. » ou «.. /..», en fonction de son emplacement par rapport au dossier de solution.

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

Le fichier *mydockercompose. yml* doit ressembler à ceci, avec le contexte de build défini sur le chemin d’accès relatif du dossier de solution (dans ce cas, `..` ).

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

## <a name="overriding-visual-studios-docker-compose-configuration"></a>Substitution de la configuration de Docker Compose de Visual Studio

Vous pouvez remplacer certains paramètres en plaçant un fichier nommé *docker-compose. vs. Debug. yml* (pour le mode **rapide** ) ou *docker-compose. vs. Release. yml* (pour le mode **normal** ) dans le même répertoire que votre fichier *docker-compose. yml* . 

>[!TIP] 
>Pour connaître les valeurs par défaut de l’un de ces paramètres, consultez *docker-compose. vs. Debug. g. yml* ou *docker-compose. vs. Release. g. yml*.

### <a name="docker-compose-file-labels"></a>Étiquettes de fichier Docker Compose

 Dans *docker-compose. vs. Debug. yml* ou *docker-compose. vs. Release. yml*, vous pouvez définir des étiquettes spécifiques au remplacement comme suit :

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
|com. Microsoft. VisualStudio. Debugger. Program|Le programme est lancé au démarrage du débogage. Pour les applications .NET Core, ce paramètre est généralement **dotnet**.|
|com. Microsoft. VisualStudio. Debugger. WorkingDirectory|Répertoire utilisé comme répertoire de démarrage lors du démarrage du débogage. Ce paramètre est généralement */app* pour les conteneurs Linux ou *C:\app* pour les conteneurs Windows.|
|com. Microsoft. VisualStudio. Debugger. killprogram|Cette commande permet d’arrêter le programme débogué qui s’exécute dans le conteneur (si nécessaire).|

### <a name="customize-the-docker-build-process"></a>Personnaliser le processus de génération de l’ancrage

Vous pouvez déclarer l’étape à générer dans votre fichier dockerfile à l’aide du `target` paramètre de la `build` propriété. Ce remplacement ne peut être utilisé que dans *docker-compose. vs. Debug. yml* ou *docker-compose. vs. Release. yml* 

```yml
services:
  webapplication1:
    build:
      target: customStage
    labels:
      ...
```

### <a name="customize-the-app-startup-process"></a>Personnaliser le processus de démarrage de l’application

Vous pouvez exécuter une commande ou un script personnalisé avant de lancer votre application à l’aide du `entrypoint` paramètre et de la rendre dépendante de `DockerDevelopmentMode` . Par exemple, si vous devez configurer un certificat uniquement en mode **rapide** en exécutant `update-ca-certificates` , mais pas en mode **normal** , vous pouvez ajouter le code suivant dans **uniquement** *docker-compose. vs. Debug. yml*:

```yml
services:
  webapplication1:
    entrypoint: "sh -c 'update-ca-certificates && tail -f /dev/null'"
    labels:
      ...
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les propriétés MSBuild en général, consultez [propriétés MSBuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Voir aussi

[Propriétés de build des outils de conteneur](container-msbuild-properties.md)

[Paramètres de lancement des outils de conteneur](container-launch-settings.md)

[Propriétés réservées et connues de MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
