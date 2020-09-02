---
title: CombinePath, tâche | Microsoft Docs
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
- MSBuild, CombinePath task
- CombinePath task [MSBuild]
ms.assetid: c20edbf4-3d4f-4f66-b1d5-753a0d858ed8
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3b97714fc707d8f9174a01dcc1fe7b3b59176de2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160384"
---
# <a name="combinepath-task"></a>CombinePath, tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Combine les chemins spécifiés en un chemin unique.  
  
## <a name="task-parameters"></a>Paramètres de tâche  
 Le tableau suivant décrit les paramètres de la [tâche CombinePath](../msbuild/combinepath-task.md).  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`BasePath`|Paramètre `String` requis.<br /><br /> Chemin de base à combiner aux autres chemins. Peut être un chemin relatif, absolu ou vide.|  
|`Paths`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Liste de chemins individuels à combiner avec BasePath pour former le chemin combiné. Les chemins peuvent être relatifs ou absolus.|  
|`CombinedPaths`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Chemin combiné créé par cette tâche.|  
  
## <a name="remarks"></a>Notes  
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension> , qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task> . Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Décrites](../msbuild/msbuild-tasks.md)   
 [Référence de tâche](../msbuild/msbuild-task-reference.md)
