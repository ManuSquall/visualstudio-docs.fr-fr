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
- MSBuild (Visual C++), GetOutOfDateItems task
- GetOutOfDateItems task (MSBuild (Visual C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: e3393dd7e81fa98c49dd09a32457171286f88f18
ms.sourcegitcommit: d78821f8c353e0102b1554719f549f32dffac71b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58514968"
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