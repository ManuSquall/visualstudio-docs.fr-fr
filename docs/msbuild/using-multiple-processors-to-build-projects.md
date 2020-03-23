---
title: Utilisation de plusieurs processeurs pour générer des projets | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multiple processors
- MSBuild, multiple processor systems
ms.assetid: 49fa36c9-8e14-44f5-8a2b-34146cf6807b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5dc62112324f7ad19c47b346ac8c1e3f86570b0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631300"
---
# <a name="use-multiple-processors-to-build-projects"></a>Utiliser plusieurs processeurs pour générer des projets

MSBuild permet d’exploiter des systèmes dotés de plusieurs processeurs ou de processeurs à plusieurs cœurs. Un processus de génération séparé est créé pour chaque processeur disponible. Par exemple, si le système comporte quatre processeurs, quatre processus de génération sont créés. MSBuild peut traiter ces builds simultanément, et donc le temps de construction global est réduit. Toutefois, la génération parallèle introduit des modifications dans le déroulement du processus de génération. Cette rubrique aborde ces modifications.

## <a name="project-to-project-references"></a>Références entre projets

 Lorsque le moteur microsoft Build rencontre une référence de projet à projet (P2P) alors qu’il utilise des builds parallèles pour construire un projet, il ne construit la référence qu’une seule fois. Si deux projets ont la même référence P2P, elle n’est pas régénérée pour chaque projet. Au lieu de cela, le moteur de génération retourne la même référence P2P aux deux projets qui en dépendent. La même référence P2P est fournie aux futures demandes de la session concernant la même cible.

## <a name="cycle-detection"></a>Détection de cycle

 Fonctions de détection de cycle de la même façon que dans MSBuild 2.0, sauf que maintenant MSBuild peut signaler la détection du cycle à un moment différent ou dans la construction.

## <a name="errors-and-exceptions-during-parallel-builds"></a>Erreurs et exceptions pendant les générations parallèles

 Dans les builds parallèles, les erreurs et exceptions ne se produisent pas nécessairement aux mêmes moments que dans une build non parallèle, et quand la build d’un projet échoue, les autres builds de projet continuent. MSBuild n’arrêtera aucune construction de projet qui se construit parallèlement à celle qui a échoué. La génération d’autres projets continue jusqu’à ce qu’elles réussissent ou échouent. Toutefois, si <xref:Microsoft.Build.Framework.IBuildEngine.ContinueOnError%2A> a été activé, aucune génération ne s’arrête, même si une erreur se produit.

## <a name="c-project-vcxproj-and-solution-sln-files"></a>Fichiers de projet (.vcxproj) et de solution (.sln)

 Les deux projets C (*.vcxproj*) et les fichiers de solution (*.sln*) peuvent être transmis à la [tâche MSBuild](../msbuild/msbuild-task.md). Pour les projets C, VCWrapperProject est appelé, puis le projet interne MSBuild est créé. Pour les solutions CMD, un solutionWrapperProject est créé, puis le projet interne MSBuild est créé. Dans les deux cas, le projet qui en résulte est traité de la même façon que tout autre projet MSBuild.

## <a name="multi-process-execution"></a>Exécution de plusieurs processus

 Presque toutes les activités liées à la génération nécessitent un répertoire constant durant le processus de génération pour éviter les erreurs liées aux chemins. Par conséquent, les projets ne peuvent pas fonctionner sur différents threads dans MSBuild parce qu’ils entraîneraient la création de plusieurs répertoires.

 Pour éviter ce problème, tout en permettant des constructions multi-processeurs, MSBuild utilise « l’isolement des processus ». En utilisant l’isolement des processus, MSBuild peut créer un maximum de `n` processus, où `n` il correspond au nombre de processeurs disponibles sur le système. Par exemple, si MSBuild construit une solution sur un système qui comporte deux processeurs, alors seulement deux processus de construction sont créés. Ces processus sont réutilisés pour générer tous les projets dans la solution.

## <a name="see-also"></a>Voir aussi

- [Construire plusieurs projets en parallèle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
- [Tâches](../msbuild/msbuild-tasks.md)
