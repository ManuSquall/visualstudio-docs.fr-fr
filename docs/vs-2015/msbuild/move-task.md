---
title: Move, tâche | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 46fd157a1b4425f7a6f3c2f3ec6e6ba9d4ee1083
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504331"
---
# <a name="move-task"></a>Move, tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [déplacer la tâche](https://docs.microsoft.com/visualstudio/msbuild/move-task).  
  
  
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
  
## <a name="remarks"></a>Notes  
 Le paramètre `DestinationFolder` ou le paramètre `DestinationFiles` doit être spécifié, mais pas les deux. Si les deux paramètres sont spécifiés, la tâche échoue, et une erreur est enregistrée.  
  
 En plus des paramètres répertoriés dans le tableau, cette tâche comprend des paramètres qu’elle hérite de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)



