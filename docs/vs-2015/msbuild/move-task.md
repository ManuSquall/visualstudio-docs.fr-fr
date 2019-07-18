---
title: Move, tâche | Microsoft Docs
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
- MSBuild, Move task
- Move task [MSBuild]
ms.assetid: d1405347-1309-4f18-b565-905408093d59
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ab75ccebd618946454c3386f564e3f6199409935
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68191570"
---
# <a name="move-task"></a>Move, tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Déplace les fichiers vers un nouvel emplacement.  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche `Move`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`DestinationFiles`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie la liste de fichiers vers laquelle déplacer les fichiers sources. Cette liste est censée représenter un mappage un-à-un à la liste spécifiée dans le paramètre `SourceFiles`. Autrement dit, le premier fichier spécifié dans `SourceFiles` est déplacé au premier emplacement indiqué dans `DestinationFiles`, et ainsi de suite.|  
|`DestinationFolder`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Indique le répertoire dans lequel vous souhaitez déplacer les fichiers.|  
|`MovedFiles`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient les éléments qui ont été déplacés avec succès.|  
|`OverwriteReadOnlyFiles`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, remplace les fichiers même s’ils sont marqués comme fichiers en lecture seule.|  
|`SourceFiles`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Spécifie les fichiers à déplacer.|  
  
## <a name="remarks"></a>Remarques  
 Le paramètre `DestinationFolder` ou le paramètre `DestinationFiles` doit être spécifié, mais pas les deux. Si les deux paramètres sont spécifiés, la tâche échoue, et une erreur est enregistrée.  
  
 En plus des paramètres répertoriés dans le tableau, cette tâche comprend des paramètres qu’elle hérite de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)
