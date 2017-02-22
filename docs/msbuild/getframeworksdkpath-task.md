---
title: "GetFrameworkSdkPath Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkSdkPath"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "GetFrameworkSdkPath task [MSBuild]"
  - "MSBuild, GetFrameworkSdkPath task"
ms.assetid: 2ef82b98-02b6-40cf-a9b5-f0e882fb5064
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# GetFrameworkSdkPath Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Récupère le chemin d'accès au [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  
  
## Paramètres de la tâche  
 Le tableau suivant décrit les paramètres de la tâche `GetFrameworkSdkPath`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`FrameworkSdkVersion20Path`|Paramètre de sortie `String` en lecture seule facultatif.<br /><br /> Renvoie le chemin d'accès au Kit de développement logiciel de .NET v2.0, le cas échéant.  Sinon, retourne `String.Empty`.|  
|`FrameworkSdkVersion35Path`|Paramètre de sortie `String` en lecture seule facultatif.<br /><br /> Renvoie le chemin d'accès au Kit de développement logiciel de .NET v3.5, le cas échéant.  Sinon, retourne `String.Empty`.|  
|`FrameworkSdkVersion40Path`|Paramètre de sortie `String` en lecture seule facultatif.<br /><br /> Renvoie le chemin d'accès au Kit de développement logiciel de .NET v4.0, le cas échéant.  Sinon, retourne `String.Empty`.|  
|`Path`|Paramètre de sortie `String` facultatif.<br /><br /> Contient le chemin d'accès au Kit de développement logiciel de .NET le plus récent, le cas échéant.  Sinon, retourne `String.Empty`.|  
  
## Notes  
 En plus des paramètres énumérés ci\-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui hérite elle\-même de la classe <xref:Microsoft.Build.Utilities.Task>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Exemple  
 L'exemple suivant utilise la tâche `GetFrameworkSdkPath` pour stocker le chemin d'accès au [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] dans la propriété `SdkPath`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkSdkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="SdkPath" />  
        </GetFrameworkSdkPath>  
        <Message Text="$(SdkPath)"/>  
    </Target>  
</Project>  
```  
  
## Voir aussi  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)