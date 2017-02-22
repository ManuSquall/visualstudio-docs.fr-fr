---
title: "GetAssemblyIdentity Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GetAssemblyIdentity"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, GetAssemblyIdentity task"
  - "GetAssemblyIdentity task [MSBuild]"
ms.assetid: a977e072-37ad-4941-84a6-32a4483be55d
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# GetAssemblyIdentity Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Récupère les identités d'assembly des fichiers spécifiés et renvoie les informations d'identité.  
  
## Paramètres de la tâche  
 Le tableau suivant décrit les paramètres de la tâche `GetAssemblyIdentity`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`Assemblies`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient les identités d'assembly récupérées.|  
|`AssemblyFiles`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Spécifie les fichiers à partir desquels récupérer les identités.|  
  
## Notes  
 Les éléments générés par le paramètre `Assemblies` contiennent des entrées de métadonnées d'élément appelées `Version`, `PublicKeyToken` et `Culture`.  
  
 En plus des paramètres énumérés ci\-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui hérite elle\-même de la classe <xref:Microsoft.Build.Utilities.Task>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Exemple  
 L'exemple suivant récupère l'identité des fichiers spécifiés dans l'élément `MyAssemblies` et les renvoie dans l'élément `MyAssemblyIdentities`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyAssemblies Include="File1.dll;File2.dll" />  
    </ItemGroup>  
  
    <Target Name="RetrieveIdentities>  
        <GetAssemblyIdentity  
            AssemblyFiles="@(MyAssemblies)"  
            <Output  
                TaskParameter="Assemblies"  
                ItemName="MyAssemblyIdentities"  
    </Target>  
  
</Project>  
```  
  
## Voir aussi  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)