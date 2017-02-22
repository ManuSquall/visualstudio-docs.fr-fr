---
title: "WriteLinesToFile Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#WriteLinesToFile"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "WriteLinesToFile task [MSBuild]"
  - "MSBuild, WriteLinesToFile task"
ms.assetid: 9c8862ac-8da5-4437-9430-ecc30421f1c9
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# WriteLinesToFile Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Écrit les chemins d'accès des éléments spécifiés dans le fichier texte indiqué.  
  
## Paramètres de la tâche  
 Le tableau suivant décrit les paramètres de la tâche `WriteLinestoFile`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`File`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> obligatoire.<br /><br /> Spécifie le fichier dans lequel écrire les éléments.|  
|`Lines`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` optionnel.<br /><br /> Spécifie les éléments à écrire dans le fichier.|  
|`Overwrite`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, la tâche substitue tout contenu existant dans le fichier.|  
|`Encoding`|Paramètre `String` facultatif.<br /><br /> Sélectionne l'encodage de caractères, par exemple « Unicode ».  Voir aussi <xref:System.Text.Encoding>.|  
  
## Notes  
 Si `Overwrite` a la valeur `true`, cela crée un nouveau fichier, écrit le contenu dans le fichier, puis ferme le fichier.  Si le fichier cible existe déjà, il est remplacé.  Si `Overwrite` a la valeur `false`, ajoute le contenu au fichier, en créant le fichier cible s'il n'existe pas déjà.  
  
 En plus des paramètres énumérés ci\-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui hérite elle\-même de la classe <xref:Microsoft.Build.Utilities.Task>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Exemple  
 L'exemple suivant utilise la tâche `WriteLinesToFile` pour écrire les chemins d'accès des éléments de la collection d'éléments `MyItems` dans le fichier spécifié par la collection d'éléments `MyTextFile`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyTextFile Include="Items.txt"/>  
        <MyItems Include="*.cs"/>  
    </ItemGroup>  
  
    <Target Name="WriteToFile">  
        <WriteLinesToFile  
            File="@(MyTextFile)"  
            Lines="@(MyItems)"  
            Overwrite="true"  
            Encoding="Unicode"/>  
    </Target>  
  
</Project>  
```  
  
## Voir aussi  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)