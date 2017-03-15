---
title: "AssignTargetPath Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 0e830e31-3bcf-4259-b2a8-a5df49b92d51
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# AssignTargetPath Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette tâche accepte une liste de fichiers et ajoute des attributs `<TargetPath>` s'ils ne sont pas déjà indiqués.  
  
## Paramètres de la tâche  
 Le tableau suivant décrit les paramètres de la tâche `AssignTargetPath`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`RootFolder`|Paramètre d'entrée `string` facultatif.<br /><br /> Contient le chemin d'accès au dossier qui contient les liens cibles.|  
|`Files`|Paramètre d'entrée <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient la liste entrante de fichiers.|  
|`AssignedFiles`|Facultatif<br /><br /> Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Contient la liste résultante de fichiers.|  
  
## Notes  
 En plus des paramètres énumérés ci\-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui hérite elle\-même de la classe <xref:Microsoft.Build.Utilities.Task>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Exemple  
 L'exemple suivant exécute la tâche `AssignTargetPath` pour configurer un projet.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyProject">  
        <AssignTargetPath  
RootFolder="Resources"  
            Files="@(ResourceFiles)"  
            <Output TaskParameter="AssignedFiles"  
                ItemName="OutAssignedFiles"/>  
        </AssignTargetPath>  
    </Target>  
</Project>  
```  
  
## Voir aussi  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)