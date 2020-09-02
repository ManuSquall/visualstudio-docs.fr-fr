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
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d95b6e7d4197487adc13050572ac31310701c759
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75595343"
---
# <a name="custombuild-task"></a>Tâche CustomBuild

Encapsule l’outil compilateur Microsoft C++, cmd.exe. Cette classe est dérivée de [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md), mais elle n’utilise pas le suivi de fichiers pour découvrir les dépendances de fichiers. Toutes les dépendances doivent être explicitement spécifiées avec AdditionalDependencies pour que la génération incrémentielle fonctionne correctement.

## <a name="parameters"></a>Paramètres

Le tableau ci-dessous décrit les paramètres de la tâche **CustomBuild**.

|Paramètre|Description|
|---------------|-----------------|
|**BuildSuffix**|Paramètre de **chaîne** facultatif.|
|**Sources**|Paramètre **ITaskItem []** obligatoire.|
|**TrackerLogDirectory**|Paramètre de **chaîne** facultatif.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
