---
title: "MakeDir Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#MakeDir"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MakeDir task [MSBuild]"
  - "MSBuild, MakeDir task"
ms.assetid: bc951577-1bfb-4100-b1f1-bc8278c45bf7
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# MakeDir Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Crée des répertoires et, le cas échéant, des répertoires parents existants.  
  
## Paramètres  
 Le tableau suivant décrit les paramètres de la tâche `MakeDir`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`Directories`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Ensemble de répertoires à créer.|  
|`DirectoriesCreated`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Répertoires créés par cette tâche.  Si certains répertoires n'ont pas pu être créés, il est possible que ce paramètre ne contienne pas tous les éléments passés dans le paramètre `Directories`.|  
  
## Notes  
 En plus des paramètres énumérés ci\-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui hérite elle\-même de la classe <xref:Microsoft.Build.Utilities.Task>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Exemple  
 L'exemple de code suivant utilise la tâche `MakeDir` pour créer le répertoire spécifié par la propriété `OutputDirectory`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <OutputDirectory>\Output\</OutputDirectory>  
    </PropertyGroup>  
  
    <Target Name="CreateDirectories">  
        <MakeDir  
            Directories="$(OutputDirectory)"/>  
    </Target>  
  
</Project>  
```  
  
## Voir aussi  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)