---
title: Tâche ParallelCustomBuild | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.parallelcustombuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), ParallelCustomBuild task
- ParallelCustomBuild task (MSBuild (Visual C++))
author: mikeblome
ms.author: Michael.Blome
ms.workload:
- multiple
ms.openlocfilehash: 506ead6680bd9a0aaaf38d6959da02a14dfee337
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58070372"
---
# <a name="parallelcustombuild-task"></a>Tâche ParallelCustomBuild

Exécutez des instances parallèles de la [tâche CustomBuild](../msbuild/custombuild-task.md).

## <a name="parameters"></a>Paramètres

Le tableau ci-dessous décrit les paramètres de la tâche **ParallelCustomBuild**.

|Paramètre|Description|
|---------------|-----------------|
|**BreakOnFirstFailure**|Paramètre **booléen** facultatif.|
|**MaxItemsInBatch**|Paramètre **Entier** facultatif.|
|**MaxProcesses**|Paramètre **Entier** facultatif.|
|**Sources**|Paramètre **ITaskItem[]** obligatoire.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)