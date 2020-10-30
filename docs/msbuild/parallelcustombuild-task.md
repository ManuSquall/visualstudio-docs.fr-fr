---
title: Tâche ParallelCustomBuild | Microsoft Docs
description: Découvrez comment MSBuild utilise la tâche ParallelCustomBuild pour exécuter des instances parallèles de la tâche CustomBuild.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f4491d0a5e9c9d3a2554bd32211fd1fa8f7be2d2
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048893"
---
# <a name="parallelcustombuild-task"></a>Tâche ParallelCustomBuild

Exécutez des instances parallèles de la [tâche CustomBuild](../msbuild/custombuild-task.md).

## <a name="parameters"></a>Paramètres

Le tableau ci-dessous décrit les paramètres de la tâche **ParallelCustomBuild** .

|Paramètre|Description|
|---------------|-----------------|
|**BreakOnFirstFailure**|Paramètre **booléen** facultatif.|
|**MaxItemsInBatch**|Paramètre **Entier** facultatif.|
|**MaxProcesses**|Paramètre **Entier** facultatif.|
|**Sources**|Paramètre **ITaskItem []** obligatoire.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)