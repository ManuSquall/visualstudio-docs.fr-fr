---
title: "Parameter Element | Microsoft Docs"
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
  - "Parameter element [MSBuild]"
  - "<Parameter> element [MSBuild]"
ms.assetid: b273afff-b500-4e97-8cfd-31f39fa64a51
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# Parameter Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contient des informations sur un paramètre spécifique pour une tâche générée par une `UsingTask` `TaskFactory`.  Le nom de l'élément est le nom du paramètre.  Pour plus d'informations, consultez [UsingTask Element \(MSBuild\)](../msbuild/usingtask-element-msbuild.md).  
  
## Syntaxe  
  
```  
<ParameterGroup ParameterType="SystemType"  
    Output="true/false"  
    Required="true/false" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`ParameterType`|Attribut facultatif.<br /><br /> Le type .NET du paramètre, par exemple, "System.String".|  
|`Output`|Attribut boléen facultatif.<br /><br /> Si la valeur est `true`, ce paramètre est un paramètre de sortie pour la tâche.  Par défaut, la valeur est `false`.|  
|`Required`|Attribut boléen facultatif.<br /><br /> Si la valeur est `true`, ce paramètre est un paramètre obligatoire pour la tâche.  Par défaut, la valeur est `false`.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|Contient la liste facultative des paramètres qui seront présents sur la tâche générée par une `UsingTask``TaskFactory`.|  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de l'élément `Parameter`.  
  
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