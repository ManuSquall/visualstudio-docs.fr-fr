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
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 197128fadb660ab06686d13ec304a5d9d1698070
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62778135"
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