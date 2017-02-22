---
title: "RemoveDuplicates Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#RemoveDuplicates"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, RemoveDuplicates task"
  - "RemoveDuplicates task [MSBuild]"
ms.assetid: 481cbab6-73ff-488c-aba5-2c09f9eb1e04
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# RemoveDuplicates Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Supprime les éléments en double de la collection d'éléments spécifiée.  
  
## Paramètres  
 Le tableau suivant décrit les paramètres de la tâche `RemoveDuplicates`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`Filtered`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient une collection d'éléments dont tous les doublons ont été supprimés.|  
|`Inputs`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` optionnel.<br /><br /> Collection d'éléments dont il faut supprimer les éléments en double.|  
  
## Notes  
 Cette tâche ne respecte pas la casse et ne compare pas les métadonnées des éléments lorsqu'elle identifie les doublons.  
  
 En plus des paramètres énumérés ci\-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui hérite elle\-même de la classe <xref:Microsoft.Build.Utilities.Task>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Exemple  
 L'exemple suivant utilise la tâche `RemoveDuplicates` pour supprimer les éléments en double de la collection d'éléments `MyItems`.  Au terme de l'exécution de la tâche, la collection d'éléments `FilteredItems` contient un élément.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyItems Include="MyFile.cs"/>  
        <MyItems Include="MyFile.cs">  
            <Culture>fr</Culture>  
        </MyItems>  
        <MyItems Include="myfile.cs"/>  
    </ItemGroup>  
  
    <Target Name="RemoveDuplicateItems">  
        <RemoveDuplicates  
            Inputs="@(MyItems)">  
            <Output  
                TaskParameter="Filtered"  
                ItemName="FilteredItems"/>  
        </RemoveDuplicates>  
    </Target>  
</Project>  
```  
  
## Voir aussi  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [MSBuild Concepts](../msbuild/msbuild-concepts.md)   
 [Tasks](../msbuild/msbuild-tasks.md)