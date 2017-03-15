---
title: "GetFrameworkPath Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkPath"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "GetFrameworkPath task [MSBuild]"
  - "MSBuild, GetFrameworkPath task"
ms.assetid: 5b7bcdd7-d4a0-442d-af29-8aadb3b10598
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# GetFrameworkPath Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Récupère le chemin d'accès aux assemblys [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## Paramètres de la tâche  
 Le tableau suivant décrit les paramètres de la tâche `GetFrameworkPath`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`FrameworkVersion11Path`|Paramètre de sortie `String` facultatif.<br /><br /> Contient le chemin d'accès aux assemblys de .NET Framework version 1.1, le cas échéant.  Sinon, retourne `null`.|  
|`FrameworkVersion20Path`|Paramètre de sortie `String` facultatif.<br /><br /> Contient le chemin d'accès aux assemblys de .NET Framework version 2.0, le cas échéant.  Sinon, retourne `null`.|  
|`FrameworkVersion30Path`|Paramètre de sortie `String` facultatif.<br /><br /> Contient le chemin d'accès aux assemblys de .NET Framework version 3.0, le cas échéant.  Sinon, retourne `null`.|  
|`FrameworkVersion35Path`|Paramètre de sortie `String` facultatif.<br /><br /> Contient le chemin d'accès aux assemblys de .NET Framework version 3.5, le cas échéant.  Sinon, retourne `null`.|  
|`FrameworkVersion40Path`|Paramètre de sortie `String` facultatif.<br /><br /> Contient le chemin d'accès aux assemblys de .NET Framework version 4.0, le cas échéant.  Sinon, retourne `null`.|  
|`Path`|Paramètre de sortie `String` facultatif.<br /><br /> Contient le chemin d'accès aux assemblys du .NET Framework le plus récent, le cas échéant.  Sinon, retourne `null`.|  
  
## Notes  
 Si plusieurs versions du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] sont installées, cette tâche retourne la version sur laquelle [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] est conçu pour fonctionner.  
  
 En plus des paramètres énumérés ci\-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui hérite elle\-même de la classe <xref:Microsoft.Build.Utilities.Task>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Exemple  
 L'exemple suivant utilise la tâche `GetFrameworkPath` pour stocker le chemin d'accès au [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] dans la propriété `FrameworkPath`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="FrameworkPath" />  
        </GetFrameworkPath>  
    </Target>  
</Project>  
```  
  
## Voir aussi  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)