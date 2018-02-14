---
title: "RemoveDir, tâche | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RemoveDir
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- RemoveDir task [MSBuild]
- MSBuild, RemoveDir task
ms.assetid: 7ab214be-26b2-4bcd-9de8-c1b2091c0b74
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 6183f244483eba46f729bad2880a3bab4c72a6a8
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="removedir-task"></a>RemoveDir, tâche
Supprime les répertoires spécifiés ainsi que tous leurs fichiers et sous-répertoires.  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche `RemoveDir` .  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`Directories`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Spécifie les répertoires à supprimer.|  
|`RemovedDirectories`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient les répertoires qui ont été supprimés.|  
  
## <a name="remarks"></a>Notes  
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant supprime les répertoires spécifiés par les propriétés `OutputDirectory` et `DebugDirectory`. Ces chemins sont traités comme étant relatifs au répertoire du projet.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2005">  
  
    <PropertyGroup>  
        <OutputDirectory>\Output\</OutputDirectory>  
        <DebugDirectory>\Debug\</DebugDirectory>  
    </PropertyGroup>  
  
    <Target Name="RemoveDirectories">  
        <RemoveDir  
            Directories="$(OutputDirectory);$(DebugDirectory)" />  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)