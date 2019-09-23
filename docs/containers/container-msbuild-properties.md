---
title: Propriétés de build des outils de conteneur Visual Studio
author: ghogen
description: Vue d’ensemble du processus de génération des outils de conteneur
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 4bc6cb4221d85bd43b98b2ac36c34c919937960b
ms.sourcegitcommit: 3cda0d58c5cf1985122b8977b33a171c7359f324
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70312124"
---
# <a name="container-tools-build-properties"></a>Propriétés de build des outils de conteneur

Vous pouvez personnaliser la façon dont Visual Studio génère vos projets de conteneur en définissant les propriétés utilisées par MSBuild pour générer votre projet. Par exemple, vous pouvez modifier le nom du fichier dockerfile, spécifier des balises et des étiquettes pour vos images, fournir des arguments supplémentaires passés aux commandes de l’ancrage et contrôler si Visual Studio effectue certaines optimisations de performances telles que la génération en dehors de environnement de conteneur. Vous pouvez également définir des propriétés de débogage telles que le nom de l’exécutable à lancer et les arguments de ligne de commande à fournir.

Pour définir la valeur d’une propriété, modifiez le fichier projet. Par exemple, supposons que votre fichier dockerfile soit nommé *MyDockerfile*. Vous pouvez définir la `DockerfileFile` propriété dans le fichier projet comme suit.

```xml
<PropertyGroup>
   <DockerfileFile>MyDockerfile</DockerfileFile>
</PropertyGroup>
```

Vous pouvez ajouter le paramètre de propriété à un `PropertyGroup` élément existant, ou s’il n’y en a pas `PropertyGroup` , créer un nouvel élément.

Le tableau suivant présente les propriétés MSBuild disponibles pour les projets de conteneur.

| Nom de la propriété | Description | Valeur par défaut  |
|---------------|-------------|----------------|
| DockerfileFile | Décrit le fichier dockerfile par défaut qui sera utilisé pour générer/exécuter le conteneur pour le projet. Il peut également s’agir d’un chemin d’accès. | Dockerfile |
| DockerfileTag | Balise qui sera utilisée lors de la génération de l’image de l’ancrage. Lors du débogage, un «  :d ev » est ajouté à la balise. | Nom de l’assembly après la suppression des caractères non alphanumériques avec les règles suivantes : <br/> Si la balise résultante est de type numeric, alors « image » est insérée en tant que préfixe (par exemple, image2314) <br/> Si la balise résultante est une chaîne vide, l’expression « image » est utilisée en tant que balise. |
| DockerContext | Contexte par défaut utilisé lors de la génération de l’image de l’ancrage. | Défini par Visual Studio. |
| ContainerDevelopmentMode | Contrôle si l’optimisation « génération sur hôte » (débogage « mode rapide ») est activée.  Les valeurs autorisées sont **rapide** et **normale**. | Rapide |
| DockerDefaultTargetOS | Le système d’exploitation cible par défaut utilisé lors de la génération de l’image de l’ancrage. | Défini par Visual Studio. |
| DockerImageLabels | Ensemble d’étiquettes par défaut appliqué à l’image de l’ancrage. | com. Microsoft. created-by = Visual-Studio ; com. Microsoft. Visual-Studio. Project-Name = $ (MSBuildProjectName) |
| ContainerVsDbgPath | Chemin d’accès du débogueur VSDBG. | `%USERPROFILE%\vsdbg\vs2017u5` |
| DockerfileBuildArguments | Arguments supplémentaires passés à la commande de génération de l’amarrage. | Non applicable. |
| DockerfileRunArguments | Arguments supplémentaires passés à la commande d’exécution de la station d’accueil. | Non applicable. |
| DockerfileRunEnvironmentFiles | Liste délimitée par des points-virgules des fichiers d’environnement appliqués lors de l’exécution de l’amarrage. | Non applicable. |
| DockerfileFastModeStage | Étape fichier dockerfile (cible) à utiliser lors de la génération de l’image en mode débogage. | Première étape trouvée dans le fichier dockerfile (base) |
| DockerDebuggeeProgram | Lors du débogage, le débogueur est invité à lancer ce fichier exécutable. | Pour les projets .NET Core : DotNet, ASP.NET .NET Framework Projects : Non applicable (IIS est toujours utilisé) |
| DockerDebuggeeArguments | Lors du débogage, le débogueur est invité à passer ces arguments à l’exécutable lancé. | Non applicable aux projets de .NET Framework ASP.NET |
| DockerDebuggeeWorkingDirectory | Lors du débogage, le débogueur est invité à utiliser ce chemin d’accès comme répertoire de travail. | C:\app (Windows) ou/App (Linux) |
| DockerDebuggeeKillProgram | Cette commande permet de terminer le processus en cours d’exécution dans un conteneur. | Non applicable aux projets de .NET Framework ASP.NET |

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les propriétés MSBuild en général, consultez [propriétés MSBuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Voir aussi

[Docker Compose les propriétés de build](docker-compose-properties.md)

[Paramètres de lancement des outils de conteneur](container-launch-settings.md)

[Propriétés réservées et connues de MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
