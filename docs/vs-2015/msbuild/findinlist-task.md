---
title: FindInList, tâche | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f5011d1b9e83b379be8eb4b23ec6a7aac649ef9a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54774555"
---
# <a name="findinlist-task"></a>FindInList, tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Dans une liste spécifiée, recherche un élément associé à la spécification d’éléments (itemspec) correspondante.  
  
## <a name="parameters"></a>Paramètres  
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
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)
