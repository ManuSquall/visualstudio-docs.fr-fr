---
title: "FindUnderPath Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#FindUnderPath"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, FindUnderPath task"
  - "FindUnderPath task [MSBuild]"
ms.assetid: 3c6d58b0-36e8-47aa-bfca-b73dd2045d91
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# FindUnderPath Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Détermine les éléments de la collection d'éléments spécifiée dont les chemins d'accès figurent dans le dossier spécifié ou sous celui\-ci.  
  
## Paramètres  
 Le tableau suivant décrit les paramètres de la tâche `FindUnderPath`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`Files`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` optionnel.<br /><br /> Spécifie les fichiers dont les chemins d'accès doivent être comparés au chemin d'accès spécifié par le paramètre `Path`.|  
|`InPath`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient les éléments trouvés sous le chemin d'accès spécifié.|  
|`OutOfPath`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient les éléments introuvables sous le chemin d'accès spécifié.|  
|`Path`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> obligatoire.<br /><br /> Spécifie le chemin d'accès au dossier à utiliser comme référence.|  
|`UpdateToAbsolutePaths`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est true, les chemins d'accès des éléments de sortie sont mis à jour pour correspondre à des chemins absolus.|  
  
## Notes  
 En plus des paramètres énumérés ci\-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui hérite elle\-même de la classe <xref:Microsoft.Build.Utilities.Task>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Exemple  
 L'exemple suivant utilise la tâche `FindUnderPath` pour déterminer si les fichiers contenus dans l'élément `MyFiles` possèdent des chemins d'accès sous le chemin d'accès spécifié par la propriété `SearchPath`.  Au terme de la tâche, l'élément `FilesNotFoundInPath` contient le fichier `File1.txt` et l'élément `FilesFoundInPath` contient le fichier `File2.txt`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <MyFiles Include="C:\File1.txt" />  
        <MyFiles Include="C:\Projects\MyProject\File2.txt" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <SearchPath>C:\Projects\MyProject</SearchPath>  
    </PropertyGroup>  
  
    <Target Name="FindFiles">  
        <FindUnderPath  
            Files="@(MyFiles)"  
            Path="$(SearchPath)">  
            <Output  
                TaskParameter="InPath"  
                ItemName="FilesFoundInPath" />  
            <Output  
                TaskParameter="OutOfPath"  
                ItemName="FilesNotFoundInPath" />  
        </FindUnderPath>  
    </Target>  
  
</Project>  
```  
  
## Voir aussi  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Tasks](../msbuild/msbuild-tasks.md)   
 [MSBuild Concepts](../msbuild/msbuild-concepts.md)