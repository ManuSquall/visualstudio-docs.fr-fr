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
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 54623ab1c58d85de55c5b8a24384bf0be46f1a61
ms.sourcegitcommit: d78821f8c353e0102b1554719f549f32dffac71b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58515124"
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