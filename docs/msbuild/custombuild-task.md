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
ms.openlocfilehash: 04f33f3852f051e1f492cb2b6dca44fcdb260e11
ms.sourcegitcommit: 32144a09ed46e7223ef7dcab647a9f73afa2dd55
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2019
ms.locfileid: "67587016"
---
# <a name="custombuild-task"></a>Tâche CustomBuild

Inclut l’outil Compilateur Visual C++, cmd.exe, dans un wrapper. Cette classe est dérivée de [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md), mais elle n’utilise pas le suivi de fichiers pour découvrir les dépendances de fichiers. Toutes les dépendances doivent être explicitement spécifiées avec AdditionalDependencies pour que la génération incrémentielle fonctionne correctement.

## <a name="parameters"></a>Paramètres

Le tableau ci-dessous décrit les paramètres de la tâche **CustomBuild**.

|Paramètre|Description|
|---------------|-----------------|
|**BuildSuffix**|Paramètre de **chaîne** facultatif.|
|**Sources**|Paramètre **ITaskItem[]** obligatoire.|
|**TrackerLogDirectory**|Paramètre de **chaîne** facultatif.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
