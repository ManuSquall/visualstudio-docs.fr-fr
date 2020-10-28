---
title: Tâche CustomBuild | Microsoft Docs
description: Cet article décrit la tâche CustomBuild MSBuild, qui est utilisée par MSBuild pour prendre en charge la personnalisation du processus de génération C++.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 640c1e6ae286b45f8700709829140093452a9491
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796548"
---
# <a name="custombuild-task"></a>Tâche CustomBuild

Encapsule l’outil compilateur Microsoft C++, cmd.exe. Cette classe est dérivée de [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md), mais elle n’utilise pas le suivi de fichiers pour découvrir les dépendances de fichiers. Toutes les dépendances doivent être explicitement spécifiées avec AdditionalDependencies pour que la génération incrémentielle fonctionne correctement.

## <a name="parameters"></a>Paramètres

Le tableau ci-dessous décrit les paramètres de la tâche **CustomBuild** .

|Paramètre|Description|
|---------------|-----------------|
|**BuildSuffix**|Paramètre de **chaîne** facultatif.|
|**Sources**|Paramètre **ITaskItem []** obligatoire.|
|**TrackerLogDirectory**|Paramètre de **chaîne** facultatif.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
