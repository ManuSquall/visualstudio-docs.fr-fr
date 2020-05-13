---
title: Visual Studio Container Tools Docker Compose créer des réglages
author: ghogen
description: Aperçu du processus de construction des outils de conteneurs
ms.author: ghogen
ms.date: 08/12/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 85cb8745a14439cfb09036a1bc96e6bd0fa15ae4
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "79988519"
---
# <a name="docker-compose-build-properties"></a>Docker Compose construit des propriétés

En plus des propriétés qui contrôlent les différents projets Docker, décrits dans [Container Tools construire des propriétés](container-msbuild-properties.md), vous pouvez également personnaliser la façon dont Visual Studio construit vos projets Docker Compose en définissant les propriétés Docker Compose que MSBuild utilise pour construire votre solution. Vous pouvez également contrôler la façon dont le debugger Visual Studio gère vos applications Docker Compose en définissant des étiquettes de fichiers dans les fichiers de configuration Docker Compose.

## <a name="how-to-set-the-msbuild-properties"></a>Comment définir les propriétés MSBuild

Pour définir la valeur d’une propriété, modifiez le fichier du projet. Pour les propriétés Docker Compose, ce dossier de projet est celui avec une extension .dcproj, sauf indication contraire dans le tableau dans la section suivante. Par exemple, supposons que vous souhaitez spécifier pour lancer le navigateur lorsque vous commencez à débogage. Vous pouvez `DockerLaunchAction` définir la propriété dans le fichier de projet .dcproj comme suit.

```xml
<PropertyGroup>
   <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
</PropertyGroup>
```

Vous pouvez ajouter le paramètre de propriété à un élément existant, `PropertyGroup` ou s’il n’y en a pas, créer un nouvel `PropertyGroup` élément.

## <a name="docker-compose-msbuild-properties"></a>Propriétés MSBuild Docker Compose

Le tableau suivant montre les propriétés MSBuild disponibles pour les projets Docker Compose.

| Nom de la propriété | Emplacement | Description | Valeur par défaut  |
|---------------|----------|-------------|----------------|
|AutresComposFilePaths|dcproj (en)|Spécifie des fichiers de composition supplémentaires dans une liste semi-alignée à envoyer à docker-compos.exe pour toutes les commandes. Les chemins relatifs du fichier de projet docker-compose (dcproj) sont autorisés.|-|
|DockerComposeBaseFilePath (en)|dcproj (en)|Spécifie la première partie des noms de fichiers des fichiers docker-compose, sans l’extension *.yml.* Par exemple : <br>1. DockerComposeBaseFilePath - null/indéfini: utilisez le chemin de fichier de base *docker-composer*, et les fichiers seront nommés *docker-compose.yml* et *docker-compose.override.yml*<br>2. DockerComposeBaseFilePath - *mydockercompose*: les fichiers seront nommés *mydockercompose.yml* et *mydockercompose.override.yml*<br> 3. DockerComposeBaseFilePath . *. Mydockercompose*: les fichiers seront en hausse d’un niveau. |docker-composer|
|DockerComposeBuildArguments|dcproj (en)|Spécifie les paramètres supplémentaires `docker-compose build` à transmettre à la commande. Par exemple : `--parallel --pull` |
|DockerComposDownArguments|dcproj (en)|Spécifie les paramètres supplémentaires `docker-compose down` à transmettre à la commande. Par exemple : `--timeout 500`|-|  
|DockerComposeProjectPath|csproj ou vbproj|Le chemin relatif vers le fichier du projet docker-compose (dcproj). Définissez cette propriété lors de la publication du projet de service pour trouver les paramètres associés de construction d’image stockés dans le fichier docker-compose.yml.|-|
|DockerComposUpArguments|dcproj (en)|Spécifie les paramètres supplémentaires `docker-compose up` à transmettre à la commande. Par exemple : `--timeout 500`|-|
|DockerDevelopmentMode|dcproj (en)| Contrôle si l’optimisation du « build-on-host » (débugging en mode rapide) est activée.  Les valeurs autorisées sont **rapides** et **régulières**. | Rapide |
|DockerLaunchAction| dcproj (en) | Spécifie l’action de lancement pour effectuer sur F5 ou Ctrl-F5.  Les valeurs autorisées ne sont aucune, LaunchBrowser et LaunchWCFTestClient|None|
|DockerLaunchBrowser (en)| dcproj (en) | Indique s’il faut lancer le navigateur. Ignoré si DockerLaunchAction est spécifié. | False |
|DockerServiceName (en)| dcproj (en)|Si DockerLaunchAction ou DockerLaunchBrowser sont spécifiés, alors DockerServiceName est le nom du service qui doit être lancé.  Utilisez cette propriété pour déterminer lequel des projets potentiellement nombreux qu’un fichier docker-compose peut référence sera lancé.|-|
|DockerServiceUrl (en)| dcproj (en) | L’URL à utiliser lors du lancement du navigateur.  Les jetons de remplacement valides sont « ServiceIPAddress », « ServicePort » et « Scheme ».  Par exemple : 'Scheme'://'ServiceIPAddress': 'ServicePort'|-|
|DockerTargetOS (en)| dcproj (en) | L’OS cible utilisée lors de la construction de l’image Docker.|-|

## <a name="example"></a> Exemple

Si vous modifiez l’emplacement des `DockerComposeBaseFilePath` fichiers de composition docker, en définissant à un chemin relatif, alors vous devez également vous assurer que le contexte de construction est changé de sorte qu’il fait référence au dossier de solution. Par exemple, si votre fichier de composition docker est un dossier appelé *DockerComposeFiles*, puis docker compose fichier devrait définir le contexte de construction à ".." ou ".. /..", selon l’endroit où il est par rapport au dossier de solution.

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

Le fichier *mydockercompose.yml* devrait ressembler à ceci, avec le contexte de construction réglé `..`à la trajectoire relative du dossier de solution (dans ce cas, ).

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
> DockerComposeBuildArguments, DockerComposeDownArguments et DockerComposeUpArguments sont nouveaux dans Visual Studio 2019 version 16.3.

## <a name="docker-compose-file-labels"></a>Étiquettes de fichiers Docker Compose

Vous pouvez également remplacer certains paramètres en plaçant un fichier nommé *docker-compose.vs.debug.yml* (pour la configuration **Debug)** ou *docker-compose.vs.release.yml* (pour la configuration **de libération)** dans le même répertoire que votre fichier *docker-compose.yml.*  Dans ce fichier, vous pouvez spécifier les paramètres comme suit :

```yml
services:
  webapplication1:
    labels:
      com.microsoft.visualstudio.debuggee.workingdirectory: "C:\\my_app_folder"
```

Utilisez des citations doubles autour des valeurs, comme dans l’exemple précédent, et utilisez la barre oblique inverse comme un personnage d’évasion pour les contre-coups de relique dans les chemins.

|Nom d'étiquette|Description|
|----------|-----------|
|com.microsoft.visualstudio.debuggee.arguments|Les arguments sont passés au programme lors du démarrage de débogage. Pour les applications .NET Core, ces arguments sont généralement des voies de recherche supplémentaires pour les paquets NuGet suivies par le chemin vers l’assemblage de sortie du projet.|
|com.microsoft.visualstudio.debuggee.killprogram|Cette commande est utilisée pour arrêter le programme de débbuggee qui fonctionne à l’intérieur du conteneur (si nécessaire).|
|com.microsoft.visualstudio.debuggee.program (en anglais seulement)|Le programme a été lancé lors du démarrage du débogage. Pour les applications .NET Core, ce paramètre est généralement **dotnet**.|
|com.microsoft.visualstudio.debuggee.workingdirectory|Le répertoire utilisé comme répertoire de départ lors du démarrage de débogage. Ce paramètre est généralement */app* pour les conteneurs Linux, ou *C: 'app* pour les conteneurs Windows.|

## <a name="customize-the-app-startup-process"></a>Personnaliser le processus de démarrage de l’application

Vous pouvez exécuter une commande ou un script `entrypoint` personnalisé avant de lancer votre application en utilisant le paramètre et en la rendant dépendante de la configuration. Par exemple, si vous avez besoin de configurer un `update-ca-certificates`certificat uniquement en mode **Debug** en cours d’exécution, mais pas en mode **Libération,** vous pouvez ajouter le code suivant uniquement dans *docker-compose.vs.debug.yml*:

```yml
services:
  webapplication1:
    entrypoint: "sh -c 'update-ca-certificates && tail -f /dev/null'"
    labels:
      ...
```

Si vous omettez le *docker-compose.vs.release.yml* ou *docker-compose.vs.debug.yml* puis Visual Studio en génère un en fonction des paramètres par défaut.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les propriétés MSBuild en général, voir [MSBuild Properties](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Voir aussi

[Les outils de conteneur construisent des propriétés](container-msbuild-properties.md)

[Paramètres de lancement d’outils de conteneurs](container-launch-settings.md)

[MSBuild, propriétés réservées et connues](../msbuild/msbuild-reserved-and-well-known-properties.md)
