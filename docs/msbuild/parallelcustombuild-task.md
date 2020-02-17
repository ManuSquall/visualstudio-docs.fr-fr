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
- MSBuild (C++), ParallelCustomBuild task
- ParallelCustomBuild task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: 0d8a171d393f629d0b6ab3a7fc61ad37862b0da1
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77279266"
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