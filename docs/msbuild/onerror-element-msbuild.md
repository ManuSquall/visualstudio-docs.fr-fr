---
title: "OnError Element (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#OnError"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "OnError Element [MSBuild]"
  - "<OnError Element [MSBuild]"
ms.assetid: 765767d3-ecb7-4cd9-ba1e-d9468964dddc
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# OnError Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Entraîne l'exécution d'une ou plusieurs cibles si l'attribut `ContinueOnError` est `false` pour une tâche ayant échoué.  
  
## Syntaxe  
  
```  
<OnError ExecuteTargets="TargetName"  
    Condition="'String A'=='String B'" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Condition`|Attribut facultatif.<br /><br /> Condition à évaluer.  Pour plus d’informations, consultez [Conditions](../msbuild/msbuild-conditions.md).|  
|`ExecuteTargets`|Attribut requis.<br /><br /> Cibles à exécuter si une tâche échoue.  Utilisez des points\-virgules pour séparer plusieurs cibles.  Les différentes cibles sont exécutées dans l'ordre spécifié.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Cible](../msbuild/target-element-msbuild.md)|Élément conteneur pour les tâches [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
  
## Notes  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] exécute l'élément d' `OnError` si l'une des tâches d'élément d' `Target` échoue avec l'attribut d' `ContinueOnError` à `ErrorAndStop` \(ou à `false`\).  Lorsque la tâche échoue, les cibles spécifiées dans l'attribut `ExecuteTargets` sont exécutées.  Si la cible comporte plusieurs éléments `OnError`, les éléments `OnError` sont exécutés séquentiellement lorsque la tâche échoue.  
  
 Pour plus d'informations sur l'attribut d' `ContinueOnError` , consultez [Task Element \(MSBuild\)](../msbuild/task-element-msbuild.md).  Pour plus d'informations sur les cibles, consultez [Targets](../msbuild/msbuild-targets.md).  
  
## Exemple  
 Le code suivant exécute les tâches `TaskOne` et `TaskTwo`.  Si `TaskOne` échoue, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] évalue l'élément `OnError` et exécute la cible de `OtherTarget`.  
  
```  
<Target Name="ThisTarget">  
    <TaskOne ContinueOnError="ErrorAndStop">  
    </TaskOne>  
    <TaskTwo>  
    </TaskTwo>  
    <OnError ExecuteTargets="OtherTarget" />  
</Target>  
```  
  
## Voir aussi  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)   
 [Targets](../msbuild/msbuild-targets.md)