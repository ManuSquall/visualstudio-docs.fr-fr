---
title: Utilisation de plusieurs processeurs pour générer des projets | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- multiple processors
- MSBuild, multiple processor systems
ms.assetid: 49fa36c9-8e14-44f5-8a2b-34146cf6807b
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3a590d3dc3053c5b857917dc358e32a2c7d5247c
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59651748"
---
# <a name="using-multiple-processors-to-build-projects"></a>Utilisation de plusieurs processeurs pour générer des projets
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

MSBuild permet d’exploiter des systèmes dotés de plusieurs processeurs ou de processeurs à plusieurs cœurs. Un processus de génération séparé est créé pour chaque processeur disponible. Par exemple, si le système comporte quatre processeurs, quatre processus de génération sont créés. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] peut traiter ces builds simultanément, et par conséquent la durée globale de génération est réduite. Toutefois, la génération parallèle introduit des modifications dans le déroulement du processus de génération. Cette rubrique aborde ces modifications.  
  
## <a name="project-to-project-references"></a>Références entre projets  
 Si [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] rencontre une référence entre projets (P2P) durant l’exécution de builds parallèles pour générer un projet, il génère la référence une seule fois. Si deux projets ont la même référence P2P, elle n’est pas régénérée pour chaque projet. Au lieu de cela, le moteur de génération retourne la même référence P2P aux deux projets qui en dépendent. La même référence P2P est fournie aux futures demandes de la session concernant la même cible.  
  
## <a name="cycle-detection"></a>Détection de cycle  
 La détection de cycle fonctionne de la même manière que dans [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 2.0, mais [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] peut désormais signaler la détection de cycle pendant la génération ou à un autre moment.  
  
## <a name="errors-and-exceptions-during-parallel-builds"></a>Erreurs et exceptions pendant les générations parallèles  
 Dans les builds parallèles, les erreurs et exceptions ne se produisent pas nécessairement aux mêmes moments que dans une build non parallèle, et quand la build d’un projet échoue, les autres builds de projet continuent. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] n’arrête aucune génération de projet qui s’exécute parallèlement à celle qui a échoué. La génération d’autres projets continue jusqu’à ce qu’elles réussissent ou échouent. Toutefois, si <xref:Microsoft.Build.Framework.IBuildEngine.ContinueOnError%2A> a été activé, aucune génération ne s’arrête, même si une erreur se produit.  
  
## <a name="visual-c-project-vcproj-and-solution-sln-files"></a>Fichiers projet (.vcproj) et solution (.sln) Visual C++  
 Vous pouvez passer des fichiers projet (.vcproj) et solution (.sln) [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] à la [tâche MSBuild](../msbuild/msbuild-task.md). Pour les projets [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], VCWrapperProject est appelé, puis le projet [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] interne est créé. Pour les solutions [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], un SolutionWrapperProject est créé, puis le projet [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] interne. Dans les deux cas, le projet résultant est traité comme tout autre projet [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].  
  
## <a name="multi-process-execution"></a>Exécution de plusieurs processus  
 Presque toutes les activités liées à la génération nécessitent un répertoire constant durant le processus de génération pour éviter les erreurs liées aux chemins. Les projets ne peuvent donc pas s’exécuter sur des threads différents dans [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] car ils provoqueraient la création de plusieurs répertoires.  
  
 Pour éviter ce problème tout en autorisant la génération multiprocesseur, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] utilise « l’isolation des processus ». Grâce à l’isolation des processus, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] peut créer au maximum `n` processus, où `n` représente le nombre de processeurs disponibles sur le système. Par exemple, si [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] génère une solution sur un système à deux processeurs, seuls deux processus de génération sont créés. Ces processus sont réutilisés pour générer tous les projets dans la solution.  
  
## <a name="see-also"></a>Voir aussi  
 [Génération parallèle de plusieurs projets](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)   
 [Tâches](../msbuild/msbuild-tasks.md)
