---
title: "CreateProperty Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#CreateProperty"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "CreateProperty task [MSBuild]"
  - "MSBuild, CreateProperty task"
ms.assetid: fbc31a88-62d4-43d2-b739-68ef3fac38f5
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# CreateProperty Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Remplit les propriétés avec les valeurs passées.  Cela permet de copier des valeurs d'une propriété ou d'une chaîne à l'autre.  
  
## Attributs  
 Le tableau suivant décrit les paramètres de la tâche `CreateProperty`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`Value`|Paramètre de sortie `String` facultatif.<br /><br /> Spécifie la valeur à copier vers la nouvelle propriété.|  
|`ValueSetByTask`|Paramètre de sortie `String` facultatif.<br /><br /> Contient la même valeur que le paramètre `Value`.  Utilisez ce paramètre uniquement si vous voulez éviter que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] définisse la propriété de sortie lorsqu'il ignore la cible englobante parce que les sorties sont à jour.|  
  
## Notes  
 En plus des paramètres énumérés ci\-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui hérite elle\-même de la classe <xref:Microsoft.Build.Utilities.Task>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Exemple  
 L'exemple suivant utilise la tâche `CreateProperty` pour créer la propriété `NewFile` à l'aide de la combinaison des valeurs des propriétés `SourceFilename` et `SourceFileExtension`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <SourceFilename>Module1</SourceFilename>  
        <SourceFileExtension>vb</SourceFileExtension>  
    </PropertyGroup>  
  
    <Target Name="CreateProperties">  
  
        <CreateProperty  
            Value="$(SourceFilename).$(SourceFileExtension)">  
            <Output  
                TaskParameter="Value"  
                PropertyName="NewFile" />  
        </CreateProperty>  
  
    </Target>  
  
</Project>  
```  
  
 Après avoir exécuté le projet, la valeur de la propriété `NewFile` est `Module1.vb`.  
  
## Voir aussi  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Tasks](../msbuild/msbuild-tasks.md)