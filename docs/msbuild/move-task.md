---
title: Move, tâche | Microsoft Docs
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6e2f66ea8b3a2439e3fa5ce481f0af9ec09c8207
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53917512"
---
# <a name="move-task"></a>Move (tâche)
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

 La tâche `Move` crée des dossiers pour les fichiers de destination souhaités, en fonction des besoins.

 En plus des paramètres répertoriés dans le tableau, cette tâche comprend des paramètres qu’elle hérite de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [Classe de base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
