---
title: Compilation et génération
description: Cet article décrit comment compiler et générer des projets et des solutions dans Visual Studio pour Mac
ms.topic: overview
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/03/2021
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.openlocfilehash: a24c57907afedb4f02068a071d2c9f81eb8962bb
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108640972"
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Compilation et génération dans Visual Studio pour Mac

Vous pouvez utiliser Visual Studio pour Mac pour générer des applications et créer des assemblys lors du développement de votre projet. Il est important de générer souvent votre code pour vous permettre d’identifier rapidement les incompatibilités de type, la syntaxe erronée, les mots clés mal orthographiés et d’autres erreurs au moment de la compilation. En générant et en déboguant, vous pouvez également rechercher et corriger les erreurs d’exécution, comme les erreurs liées à la logique, aux E/S et à la division par zéro.

Une génération réussie signifie que le code source contient une syntaxe correcte et que toutes les références statiques aux bibliothèques, assemblys et autres composants peuvent être résolues. Le processus de génération produit un fichier exécutable de l’application. Ce fichier exécutable peut ensuite être testé via le débogage et différents types de tests manuels et automatisés pour valider la qualité du code. Une fois que l’application a été entièrement testée, vous pouvez alors compiler une version à déployer auprès de vos clients.

Sur le Mac, vous pouvez utiliser l’une des méthodes suivantes pour générer votre application : Visual Studio pour Mac, les outils en ligne de commande MSBuild ou Azure Pipelines.

| Méthode de génération | Avantages |
| --- |--- | --- |
| Visual Studio pour Mac |- Créer des builds immédiatement et les tester dans un débogueur.<br />- Exécuter des builds multiprocesseurs pour des projets C#.<br />- Personnaliser différents aspects du système de génération. |
| Ligne de commande MSBuild| - Générer des projets sans installer Visual Studio pour Mac.<br />- Exécuter des builds multiprocesseurs pour tous les types de projets.<br />- Personnaliser la plupart des éléments du système de génération.|
| Azure Pipelines | - Automatiser votre processus de génération dans un pipeline d’intégration continue/de livraison continue.<br />- Appliquer des tests automatisés avec chaque build.<br />- Utiliser des ressources cloud virtuellement illimitées pour les processus de génération.<br />- Modifier le flux de travail de la génération et créer des activités de génération pour effectuer des tâches fortement personnalisées.|

La documentation de cette section contient plus de détails sur le processus de génération avec l’IDE. Pour créer des applications à partir de la ligne de commande sans installer Visual Studio pour Mac, vous pouvez installer le [Kit SDK .net Core](https://dotnet.microsoft.com/download)le plus récent. Pour plus d’informations sur la création d’applications à l’aide de la ligne de commande, consultez [MSBuild](/visualstudio/msbuild/msbuild). Pour plus d’informations sur la création d’applications avec Azure Pipelines, consultez [Azure Pipelines](/azure/devops/pipelines).


> [!NOTE]
> Cette rubrique s’applique à Visual Studio pour Mac. Pour Visual Studio sur Windows, consultez [Compiler et générer dans Visual Studio](/visualstudio/ide/compiling-and-building-in-visual-studio).


## <a name="building-from-the-ide"></a>Génération à partir de l'IDE

Vous pouvez utiliser Visual Studio pour Mac pour créer et exécuter des builds instantanément, tout en gardant le contrôle sur les fonctionnalités de génération. Lorsque vous créez un projet, Visual Studio pour Mac définit une configuration de build par défaut qui définit le contexte pour les builds. Vous pouvez modifier les configurations de build par défaut et également créer les vôtres. La création ou la modification de ces configurations met automatiquement à jour le fichier projet, qui est ensuite utilisé par MSBuild pour générer votre projet.

Pour plus d’informations sur la génération de projets et de solutions dans l’IDE, consultez le guide [Génération et nettoyage des projets et des solutions](building-and-cleaning-projects-and-solutions.md).

Vous pouvez aussi utiliser Visual Studio pour Mac pour :

* Changer le chemin de la sortie. Vous modifiez ce chemin dans les options de votre projet :

    ![Changer le chemin de la sortie](media/compiling-and-building-image4.png)

* Changer le niveau de détail de la sortie de la génération :

    ![Changer le niveau de détail de la génération](media/compiling-and-building-image5.png)

* Ajouter des commandes personnalisées avant, pendant ou après la génération ou le nettoyage :

    ![Ajouter des commandes personnalisées](media/compiling-and-building-image6.png)


## <a name="see-also"></a>Voir aussi

- [Compiler et générer (Visual Studio sur Windows)](/visualstudio/ide/compiling-and-building-in-visual-studio)
