---
title: ConvertToAbsolutePath, tâche | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ConvertToAbsolutePath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ConvertToAbsolutePath task [MSBuild]
- MSBuild, ConvertToAbsolutePath task
ms.assetid: f1af2cb8-b4ef-4a72-be80-22fa526c4491
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 14fa9047a4c51cb9e89dd45ff4f319523a8f82ee
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
ms.locfileid: "31578807"
---
# <a name="converttoabsolutepath-task"></a>ConvertToAbsolutePath, tâche
Convertit une référence ou un chemin relatif en chemin absolu.  
  
## <a name="task-parameters"></a>Paramètres de tâche  
 Le tableau ci-dessous décrit les paramètres de la tâche `ConvertToAbsolutePath`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`Paths`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Liste de chemins relatifs à convertir en chemins absolus.|  
|`AbsolutePaths`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Liste des chemins absolus des éléments qui ont été passés.|  
  
## <a name="remarks"></a>Notes  
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)