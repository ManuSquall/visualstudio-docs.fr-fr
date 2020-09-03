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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77631300"
---
# <a name="use-multiple-processors-to-build-projects"></a>Utiliser plusieurs processeurs pour générer des projets

MSBuild permet d’exploiter des systèmes dotés de plusieurs processeurs ou de processeurs à plusieurs cœurs. Un processus de génération séparé est créé pour chaque processeur disponible. Par exemple, si le système comporte quatre processeurs, quatre processus de génération sont créés. MSBuild peut traiter ces builds simultanément et, par conséquent, le temps de génération global est réduit. Toutefois, la génération parallèle introduit des modifications dans le déroulement du processus de génération. Cette rubrique aborde ces modifications.

## <a name="project-to-project-references"></a>Références entre projets

 Lorsque le Microsoft Build Engine rencontre une référence entre projets (P2P) alors qu’il utilise des générations parallèles pour générer un projet, il ne génère la référence qu’une seule fois. Si deux projets ont la même référence P2P, elle n’est pas régénérée pour chaque projet. Au lieu de cela, le moteur de génération retourne la même référence P2P aux deux projets qui en dépendent. La même référence P2P est fournie aux futures demandes de la session concernant la même cible.

## <a name="cycle-detection"></a>Détection de cycle

 La détection de cycle fonctionne de la même façon que dans MSBuild 2,0, à ceci près que MSBuild peut désormais signaler la détection du cycle à une heure différente ou dans la Build.

## <a name="errors-and-exceptions-during-parallel-builds"></a>Erreurs et exceptions pendant les générations parallèles

 Dans les builds parallèles, les erreurs et exceptions ne se produisent pas nécessairement aux mêmes moments que dans une build non parallèle, et quand la build d’un projet échoue, les autres builds de projet continuent. MSBuild n’arrêtera aucune génération de projet générée en parallèle avec celle qui a échoué. La génération d’autres projets continue jusqu’à ce qu’elles réussissent ou échouent. Toutefois, si <xref:Microsoft.Build.Framework.IBuildEngine.ContinueOnError%2A> a été activé, aucune génération ne s’arrête, même si une erreur se produit.

## <a name="c-project-vcxproj-and-solution-sln-files"></a>Fichiers de projet C++ (. vcxproj) et de solution (. sln)

 Les fichiers de projet C++ (*. vcxproj*) et de solution (*. sln*) peuvent être passés à la [tâche MSBuild](../msbuild/msbuild-task.md). Pour les projets C++, VCWrapperProject est appelé, puis le projet MSBuild interne est créé. Pour les solutions C++, un SolutionWrapperProject est créé, puis le projet MSBuild interne est créé. Dans les deux cas, le projet résultant est traité de la même façon que n’importe quel autre projet MSBuild.

## <a name="multi-process-execution"></a>Exécution de plusieurs processus

 Presque toutes les activités liées à la génération nécessitent un répertoire constant durant le processus de génération pour éviter les erreurs liées aux chemins. Par conséquent, les projets ne peuvent pas s’exécuter sur différents threads dans MSBuild, car ils provoquent la création de plusieurs répertoires.

 Pour éviter ce problème tout en permettant d’activer les builds multiprocesseurs, MSBuild utilise l’isolation des processus. En utilisant l’isolation des processus, MSBuild peut créer un maximum de `n` processus, où `n` est égal au nombre de processeurs disponibles sur le système. Par exemple, si MSBuild génère une solution sur un système qui a deux processeurs, seuls deux processus de génération sont créés. Ces processus sont réutilisés pour générer tous les projets dans la solution.

## <a name="see-also"></a>Voir aussi

- [Générer plusieurs projets en parallèle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
- [Tâches](../msbuild/msbuild-tasks.md)
