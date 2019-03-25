---
title: Tâche CustomBuild | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.custombuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), CustomBuild task
- CustomBuild task (MSBuild (Visual C++))
author: mikeblome
ms.author: Michael.Blome
ms.workload:
- multiple
ms.openlocfilehash: 183cdefbca29db486b84cb61f90501507e298838
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58070376"
---
# <a name="custombuild-task"></a>Tâche CustomBuild

Inclut l’outil Compilateur Visual C++, cmd.exe, dans un wrapper.

## <a name="parameters"></a>Paramètres

Le tableau ci-dessous décrit les paramètres de la tâche **CustomBuild**.

|Paramètre|Description|
|---------------|-----------------|
|**BuildSuffix**|Paramètre de **chaîne** facultatif.|
|**Sources**|Paramètre **ITaskItem[]** obligatoire.|
|**TrackerLogDirectory**|Paramètre de **chaîne** facultatif.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)