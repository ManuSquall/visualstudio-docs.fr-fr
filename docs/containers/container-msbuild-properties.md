---
title: Visual Studio Container Tools construit des propriétés
author: ghogen
description: Aperçu du processus de construction des outils de conteneurs
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 987d358abcccadf36d15593722ff55ba4b879d03
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "71950699"
---
# <a name="container-tools-build-properties"></a>Les outils de conteneur construisent des propriétés

Vous pouvez personnaliser la façon dont Visual Studio construit vos projets de conteneurs en définissant les propriétés que MSBuild utilise pour construire votre projet. Par exemple, vous pouvez changer le nom du Dockerfile, spécifier les balises et les étiquettes de vos images, fournir des arguments supplémentaires transmis aux commandes Docker et contrôler si Visual Studio fait certaines optimisations de performance telles que la construction à l’extérieur de la l’environnement des conteneurs. Vous pouvez également définir des propriétés de débogage telles que le nom de l’exécutable pour lancer, et les arguments de la ligne de commande à fournir.

Pour définir la valeur d’une propriété, modifiez le fichier du projet. Supposons, par exemple, que votre Dockerfile s’appelle *MyDockerfile*. Vous pouvez `DockerfileFile` définir la propriété dans le fichier du projet comme suit.

```xml
<PropertyGroup>
   <DockerfileFile>MyDockerfile</DockerfileFile>
</PropertyGroup>
```

Vous pouvez ajouter le paramètre de propriété à un élément existant, `PropertyGroup` ou s’il n’y en a pas, créer un nouvel `PropertyGroup` élément.

Le tableau suivant montre les propriétés MSBuild disponibles pour les projets de conteneurs. La version paquet NuGet s’applique à [Microsoft.VisualStudio.Azure.Containers.Tools.Targets](https://www.nuget.org/packages/Microsoft.VisualStudio.Azure.Containers.Tools.Targets/).

| Nom de la propriété | Description | Valeur par défaut  | Version de package NuGet|
|---------------|-------------|----------------|----------------------|
| ContainerDevelopmentMode | Contrôle si l’optimisation du « build-on-host » (débugging en mode rapide) est activée.  Les valeurs autorisées sont **rapides** et **régulières**. | Rapide |1.0.1872750 ou plus récent|
| ContainerVsDbgPath | Le chemin pour VSDBG debugger. | `%USERPROFILE%\vsdbg\vs2017u5` |1.0.1985401 ou plus récent|
| DockerDebuggeeArguments | Lors du débogage, le débogage est chargé de transmettre ces arguments à l’exécutable lancé. | Non applicable aux projets-cadres ASP.NET .NET |1.7.8 ou plus récent|
| DockerDebuggeeProgramme | Lors du débogage, le débogage est chargé de lancer ce exécutable. | Pour les projets de base .NET : dotnet, ASP.NET .NET Framework projects: Not applicable (IIS est toujours utilisé) |1.7.8 ou plus récent|
| DockerDebuggeeKillProgram | Cette commande est utilisée pour tuer le processus de fonctionnement dans un conteneur. | Non applicable aux projets-cadres ASP.NET .NET |1.7.8 ou plus récent|
| DockerDebuggeeWorkingDirectory | Lors du débogage, le débogage est chargé d’utiliser ce chemin comme répertoire de travail. | C : app (Windows) ou /app (Linux) |1.7.8 ou plus récent|
| DockerDefaultTargetOS | Le système d’exploitation cible par défaut utilisé lors de la construction de l’image Docker. | Ensemble par Visual Studio. |1.0.1985401 ou plus récent|
| DockerImageLabels (en) | L’ensemble par défaut d’étiquettes appliquées à l’image Docker. | com.microsoft.created-by-visual-studio;com.microsoft.visual-studio.project-nameMD$(MSBuildProjectName) |1.5.4 ou plus récent|
| DockerFastModeProjectMountDirectory|En **mode rapide**, cette propriété contrôle l’endroit où le répertoire de sortie du projet est monté en volume dans le conteneur en cours d’exécution.|C : app (Windows) ou /app (Linux)|1.9.2 ou plus récent|
| DockerfileBuildArguments | D’autres arguments sont passés au commandement de construction De Docker. | Non applicable. |1.0.1872750 ou plus récent|
| DockerfileContexte (en) | Le contexte par défaut utilisé lors de la construction de l’image Docker. | Ensemble par Visual Studio. |1.0.1872750 ou plus récent|
| DockerfileFastModeModeStage | L’étape Dockerfile (c’est-à-dire la cible) à utiliser lors de la construction de l’image en mode débogé. | Première étape trouvée dans le Dockerfile (base) |
| DockerfileFile (En) | Décrit le Dockerfile par défaut qui sera utilisé pour construire/exécuter le conteneur pour le projet. Cela peut être un chemin ainsi. | Dockerfile |1.0.1872750 ou plus récent|
| DockerfileRunArguments | D’autres arguments sont passés au commandement de course de Docker. | Non applicable. |1.0.1872750 ou plus récent|
| DockerfileRunEnvironmentFiles | Liste des fichiers environment sémilon-délimités appliqués pendant la course Docker. | Non applicable. |1.0.1872750 ou plus récent|
| DockerfileTag (en) | L’étiquette qui sera utilisée lors de la construction de l’image Docker. En débogage, un ":dev" est annexé à l’étiquette. | Nom de l’Assemblée après avoir dépouillé les caractères non alphanumériques avec les règles suivantes : <br/> Si l’étiquette résultante est tout numérique, alors «image» est insérée comme un préfixe (par exemple, image2314) <br/> Si l’étiquette résultante est une chaîne vide, alors "image" est utilisée comme étiquette. |1.0.1872750 ou plus récent|

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les propriétés MSBuild en général, voir [MSBuild Properties](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Voir aussi

[Docker Compose construit des propriétés](docker-compose-properties.md)

[Paramètres de lancement d’outils de conteneurs](container-launch-settings.md)

[MSBuild, propriétés réservées et connues](../msbuild/msbuild-reserved-and-well-known-properties.md)
