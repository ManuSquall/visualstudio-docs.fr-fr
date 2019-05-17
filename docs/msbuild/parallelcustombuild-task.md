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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963752"
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