---
title: FindInList, tâche | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- FindInList task [MSBuild]
- MSBuild, FindInList task
ms.assetid: d49b9f84-52a2-4242-9269-b741a7a7e9f7
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 650683c047f7df6422e25ef5b23201a2660b3125
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591123"
---
# <a name="findinlist-task"></a>FindInList (tâche)
Dans une liste spécifiée, recherche un élément associé à la spécification d’éléments (itemspec) correspondante.

## <a name="parameters"></a>Parameters
 Le tableau ci-dessous décrit les paramètres de la [tâche FindInList](../msbuild/findinlist-task.md).

|Paramètre|Description|
|---------------|-----------------|
|`CaseSensitive`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, la recherche respecte la casse ; sinon, elle ne la respecte pas. La valeur par défaut est `true`.|
|`FindLastMatch`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, retourne la dernière correspondance ; sinon, retourne la première correspondance. La valeur par défaut est `false`.|
|`ItemFound`|Paramètre de sortie en lecture seule <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Premier élément correspondant trouvé dans la liste, le cas échéant.|
|`ItemSpecToFind`|Paramètre `String` requis.<br /><br /> Spécification d’éléments (itemspec) à rechercher.|
|`List`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Liste dans laquelle rechercher la spécification d’éléments (itemspec).|
|`MatchFileNameOnly`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, effectue une comparaison avec uniquement la partie de nom de fichier de l’itemspec ; sinon, effectue une comparaison avec l’intégralité de l’itemspec. La valeur par défaut est `true`.|

## <a name="remarks"></a>Notes
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension> , qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task> . Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [Classe de base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Voir aussi
- [Tâches MSBuild](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
