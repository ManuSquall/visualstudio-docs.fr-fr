---
title: Tâche GetOutOfDateItems | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.getoutofdateitems
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), GetOutOfDateItems task
- GetOutOfDateItems task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: bfa60ff0f7e4060f5725fe54bd5950d858b86a22
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77272396"
---
# <a name="getoutofdateitems-task"></a>Tâche GetOutOfDateItems

Tâche d’assistance qui lit les tlogs anciens, écrit les nouveaux tlogs et retourne le jeu d’éléments qui ne sont pas à jour.

## <a name="parameters"></a>Paramètres

Le tableau suivant décrit les paramètres de la tâche **GetOutOfDateItems**.

|Paramètre|Description|
|---------------|-----------------|
|**CheckForInterdependencies**|Paramètre **booléen** facultatif.|
|**CommandMetadataName**|Paramètre de **chaîne** facultatif.|
|**DependenciesMetadataName**|Paramètre de **chaîne** facultatif.|
|**HasInterdependencies**|Paramètre de sortie **booléen** facultatif.|
|**OutOfDateSources**|Paramètre de sortie **ITaskItem[]** facultatif.|
|**OutputsMetadataName**|Paramètre **String** obligatoire.|
|**Sources**|Paramètre **ITaskItem[]** facultatif.|
|**TLogDirectory**|Paramètre **String** obligatoire.|
|**TLogNamePrefix**|Paramètre **String** obligatoire.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)