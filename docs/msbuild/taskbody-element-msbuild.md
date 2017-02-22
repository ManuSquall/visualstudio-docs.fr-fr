---
title: "TaskBody Element (MSBuild) | Microsoft Docs"
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
helpviewer_keywords: 
  - "TaskBody element [MSBuild]"
  - "<TaskBody> element [MSBuild]"
ms.assetid: 49d8741b-f1ea-4470-94fd-a1ac27341a6a
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# TaskBody Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contient les données passées à une `UsingTask` `TaskFactory`. Pour plus d'informations, consultez [UsingTask Element \(MSBuild\)](../msbuild/usingtask-element-msbuild.md).  
  
## Syntaxe  
  
```  
<TaskBody Evaluate="true/false" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Evaluate`|Attribut boléen facultatif.<br /><br /> Si la valeur est `true`, MSBuild évalue tous les éléments internes et développe des éléments ainsi que des propriétés avant de transmettre les informations à la `TaskFactory` lorsque la tâche est instanciée.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|Données|Le texte entre les balises `TaskBody` est envoyé mot à mot à la `TaskFactory`.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|Permet d'inscrire des tâches dans [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  Un projet peut ne contenir aucun élément `UsingTask` ou en contenir plusieurs.|  
  
## Exemple  
 L'exemple suivant montre comment utiliser l'élément `TaskBody` avec un attribut `Evaluate`.  
  
```  
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">  
       <ParameterGroup>  
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>  
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>  
              ...  
</ParameterGroup>  
       <TaskBody Evaluate="true">  
      ... Task factory-specific data ...  
       </TaskBody>  
</UsingTask>  
```  
  
## Voir aussi  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)