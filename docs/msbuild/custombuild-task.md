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
- MSBuild (C++), CustomBuild task
- CustomBuild task (MSBuild (C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 678068d1b6acc055fa65e6d0305b07152ed28695
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748112"
---
# <a name="custombuild-task"></a>Tâche CustomBuild

Encapsule l’outil C++ compilateur Microsoft, cmd. exe. Cette classe est dérivée de [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md), mais elle n’utilise pas le suivi de fichiers pour découvrir les dépendances de fichiers. Toutes les dépendances doivent être explicitement spécifiées avec AdditionalDependencies pour que la génération incrémentielle fonctionne correctement.

## <a name="parameters"></a>Paramètres

Le tableau ci-dessous décrit les paramètres de la tâche **CustomBuild**.

|Paramètre|Description|
|---------------|-----------------|
|**BuildSuffix**|Paramètre de **chaîne** facultatif.|
|**Sources**|Paramètre **ITaskItem[]** obligatoire.|
|**TrackerLogDirectory**|Paramètre de **chaîne** facultatif.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
