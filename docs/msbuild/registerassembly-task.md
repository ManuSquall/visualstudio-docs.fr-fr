---
title: "RegisterAssembly Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#RegisterAssembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, RegisterAssembly task"
  - "RegisterAssembly task [MSBuild]"
ms.assetid: ba5f19ac-6764-4d28-9b79-a86de58f8987
caps.latest.revision: 16
caps.handback.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# RegisterAssembly Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lit les métadonnées dans l'assembly spécifié et ajoute les entrées nécessaires au Registre, ce qui permet aux clients COM de créer des classes [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] de façon transparente.  Le comportement de cette tâche est similaire, sans être identique, à celui de [Regasm.exe \(Assembly Registration Tool\)](../Topic/Regasm.exe%20\(Assembly%20Registration%20Tool\).md).  
  
## Paramètres  
 Le tableau suivant décrit les paramètres de la tâche `RegisterAssembly`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`Assemblies`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Spécifie les assemblys à inscrire avec COM.|  
|`AssemblyListFile`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Contient des informations relatives à l'état entre la tâche `RegisterAssembly` et la tâche [UnregisterAssembly](../msbuild/unregisterassembly-task.md).  Cela empêche la tâche `UnregisterAssembly` de tenter l'annulation de l'inscription d'un assembly qui n'a pas été inscrit dans la tâche `RegisterAssembly`.|  
|`CreateCodeBase`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, crée une entrée de code base dans le Registre, spécifiant le chemin d'accès du fichier d'un assembly qui n'est pas installé dans le Global Assembly Cache.  Vous ne devez pas spécifier cette option si vous devez installer par la suite l'assembly que vous enregistrez dans le Global Assembly Cache.|  
|`TypeLibFiles`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie la bibliothèque de types à générer à partir de l'assembly spécifié.  La bibliothèque de types générée contient des définitions des types accessibles définis dans l'assembly.  La bibliothèque de types est générée uniquement si l'un des éléments suivants est vrai :<br /><br /> -   Il n'existe aucune bibliothèque de types de ce nom à cet emplacement.<br />-   Il existe une bibliothèque de types, mais elle est plus ancienne que l'assembly passé.<br /><br /> Si la bibliothèque de types est plus récente que l'assembly passé, aucune nouvelle bibliothèque n'est créée, mais l'assembly reste inscrit.<br /><br /> Si ce paramètre est spécifié, il doit avoir le même nombre d'éléments que le paramètre `Assemblies` ou la tâche échoue.  Si aucune entrée n'est spécifiée, la tâche prend par défaut le nom de l'assembly et modifie l'extension de l'élément en .tlb.|  
  
## Notes  
 En plus des paramètres énumérés ci\-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui hérite elle\-même de la classe <xref:Microsoft.Build.Utilities.Task>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Exemple  
 L'exemple suivant utilise la tâche `RegisterAssembly` pour inscrire l'assembly spécifié par la collection d'éléments `MyAssemblies`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyAssemblies Include="MyAssembly.dll" />  
    <ItemGroup>  
  
    <Target Name="RegisterAssemblies">  
        <RegisterAssembly  
            Assemblies="@(MyAssemblies)" >  
    </Target>  
  
</Project>  
```  
  
## Voir aussi  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)