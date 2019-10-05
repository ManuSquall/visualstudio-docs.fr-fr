---
title: Propriétés de build des outils de conteneur Visual Studio
author: ghogen
description: Vue d’ensemble du processus de génération des outils de conteneur
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 987d358abcccadf36d15593722ff55ba4b879d03
ms.sourcegitcommit: 6ae0a289f1654dec63b412bfa22035511a2ef5ad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71950699"
---
# <a name="container-tools-build-properties"></a>Propriétés de build des outils de conteneur

Vous pouvez personnaliser la façon dont Visual Studio génère vos projets de conteneur en définissant les propriétés utilisées par MSBuild pour générer votre projet. Par exemple, vous pouvez modifier le nom du fichier dockerfile, spécifier des balises et des étiquettes pour vos images, fournir des arguments supplémentaires passés aux commandes de l’ancrage et contrôler si Visual Studio effectue certaines optimisations de performances telles que la génération en dehors de environnement de conteneur. Vous pouvez également définir des propriétés de débogage telles que le nom de l’exécutable à lancer et les arguments de ligne de commande à fournir.

Pour définir la valeur d’une propriété, modifiez le fichier projet. Par exemple, supposons que votre fichier dockerfile soit nommé *MyDockerfile*. Vous pouvez définir la propriété `DockerfileFile` dans le fichier projet comme suit.

```xml
<PropertyGroup>
   <DockerfileFile>MyDockerfile</DockerfileFile>
</PropertyGroup>
```

Vous pouvez ajouter le paramètre de propriété à un élément `PropertyGroup` existant ou, si ce n’est pas le cas, créer un nouvel élément `PropertyGroup`.

Le tableau suivant présente les propriétés MSBuild disponibles pour les projets de conteneur. La version du package NuGet s’applique à [Microsoft. VisualStudio. Azure. Containers. Tools. targets](https://www.nuget.org/packages/Microsoft.VisualStudio.Azure.Containers.Tools.Targets/).

| Nom de propriété | Description | Valeur par défaut  | Version de package NuGet|
|---------------|-------------|----------------|----------------------|
| ContainerDevelopmentMode | Contrôle si l’optimisation « génération sur hôte » (débogage « mode rapide ») est activée.  Les valeurs autorisées sont **rapide** et **normale**. | Rapide |1.0.1872750 ou plus récent|
| ContainerVsDbgPath | Chemin d’accès du débogueur VSDBG. | `%USERPROFILE%\vsdbg\vs2017u5` |1.0.1985401 ou plus récent|
| DockerDebuggeeArguments | Lors du débogage, le débogueur est invité à passer ces arguments à l’exécutable lancé. | Non applicable aux projets de .NET Framework ASP.NET |1.7.8 ou plus récent|
| DockerDebuggeeProgram | Lors du débogage, le débogueur est invité à lancer ce fichier exécutable. | Pour les projets .NET Core : DotNet, ASP.NET .NET Framework Projects : Non applicable (IIS est toujours utilisé) |1.7.8 ou plus récent|
| DockerDebuggeeKillProgram | Cette commande permet de terminer le processus en cours d’exécution dans un conteneur. | Non applicable aux projets de .NET Framework ASP.NET |1.7.8 ou plus récent|
| DockerDebuggeeWorkingDirectory | Lors du débogage, le débogueur est invité à utiliser ce chemin d’accès comme répertoire de travail. | C:\app (Windows) ou/App (Linux) |1.7.8 ou plus récent|
| DockerDefaultTargetOS | Le système d’exploitation cible par défaut utilisé lors de la génération de l’image de l’ancrage. | Défini par Visual Studio. |1.0.1985401 ou plus récent|
| DockerImageLabels | Ensemble d’étiquettes par défaut appliqué à l’image de l’ancrage. | com. Microsoft. created-by = Visual-Studio ; com. Microsoft. Visual-Studio. Project-Name = $ (MSBuildProjectName) |1.5.4 ou plus récent|
| DockerFastModeProjectMountDirectory|En **mode rapide**, cette propriété contrôle l’emplacement où le répertoire de sortie du projet est monté en volume dans le conteneur en cours d’exécution.|C:\app (Windows) ou/App (Linux)|1.9.2 ou plus récent|
| DockerfileBuildArguments | Arguments supplémentaires passés à la commande de génération de l’amarrage. | Non applicable. |1.0.1872750 ou plus récent|
| DockerfileContext | Contexte par défaut utilisé lors de la génération de l’image de l’ancrage. | Défini par Visual Studio. |1.0.1872750 ou plus récent|
| DockerfileFastModeStage | Étape fichier dockerfile (cible) à utiliser lors de la génération de l’image en mode débogage. | Première étape trouvée dans le fichier dockerfile (base) |
| DockerfileFile | Décrit le fichier dockerfile par défaut qui sera utilisé pour générer/exécuter le conteneur pour le projet. Il peut également s’agir d’un chemin d’accès. | Dockerfile |1.0.1872750 ou plus récent|
| DockerfileRunArguments | Arguments supplémentaires passés à la commande d’exécution de la station d’accueil. | Non applicable. |1.0.1872750 ou plus récent|
| DockerfileRunEnvironmentFiles | Liste délimitée par des points-virgules des fichiers d’environnement appliqués lors de l’exécution de l’amarrage. | Non applicable. |1.0.1872750 ou plus récent|
| DockerfileTag | Balise qui sera utilisée lors de la génération de l’image de l’ancrage. Lors du débogage, un «  :d ev » est ajouté à la balise. | Nom de l’assembly après la suppression des caractères non alphanumériques avec les règles suivantes : <br/> Si la balise résultante est de type numeric, alors « image » est insérée en tant que préfixe (par exemple, image2314) <br/> Si la balise résultante est une chaîne vide, l’expression « image » est utilisée en tant que balise. |1.0.1872750 ou plus récent|

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les propriétés MSBuild en général, consultez [propriétés MSBuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Voir aussi

[Docker Compose les propriétés de build](docker-compose-properties.md)

[Paramètres de lancement des outils de conteneur](container-launch-settings.md)

[Propriétés réservées et connues de MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
