---
title: "Output Element (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Output"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<Output> Element [MSBuild]"
  - "Output Element [MSBuild]"
ms.assetid: 34bc7cd1-efd3-4b57-b691-4584eeb6a0e9
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Output Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Stocke les valeurs de sortie de la tâche dans les éléments et les propriétés.  
  
## Syntaxe  
  
```  
<Output TaskParameter="Parameter"  
    PropertyName="PropertyName"   
    Condition = "'String A' == 'String B'" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`TaskParameter`|Attribut requis.<br /><br /> Nom du paramètre de sortie de la tâche.|  
|`PropertyName`|L'attribut `PropertyName` ou `ItemName` est obligatoire.<br /><br /> Propriété qui reçoit la valeur du paramètre de sortie de la tâche.  Votre projet peut référencer ensuite la propriété avec la syntaxe `$(`*PropertyName*`)`.  Ce nom de propriété peut être un nouveau nom de propriété ou un nom déjà défini dans le projet.<br /><br /> Cet attribut ne peut pas être utilisé si `ItemName` est également utilisé.|  
|`ItemName`|L'attribut `PropertyName` ou `ItemName` est obligatoire.<br /><br /> Élément qui reçoit la valeur du paramètre de sortie de la tâche.  Votre projet peut référencer ensuite l'élément avec la syntaxe `@(`*ItemName*`)`.  Ce nom d'élément peut être un nouveau nom d'élément ou un nom déjà défini dans le projet.<br /><br /> Cet attribut ne peut pas être utilisé si `PropertyName` est également utilisé.|  
|`Condition`|Attribut facultatif.<br /><br /> Condition à évaluer.  Pour plus d'informations, consultez [Conditions](../msbuild/msbuild-conditions.md).|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Tâche](../msbuild/task-element-msbuild.md)|Crée et exécute une instance d'une tâche [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
  
## Exemple  
 L'exemple de code suivant illustre l'exécution de la tâche `Csc` au sein d'un élément `Target`.  Les éléments et propriétés passés dans les paramètres de la tâche sont déclarés en dehors de la portée de cet exemple.  La valeur du paramètre de sortie `OutputAssembly` est stockée dans l'élément `FinalAssemblyName` et la valeur du paramètre de sortie `BuildSucceeded` est stockée dans la propriété `BuildWorked`.  Pour plus d'informations, consultez [Tasks](../msbuild/msbuild-tasks.md).  
  
```  
<Target Name="Compile" DependsOnTargets="Resources">  
    <Csc  Sources="@(CSFile)"  
            TargetType="library"  
            Resources="@(CompiledResources)"  
            EmitDebugInformation="$(includeDebugInformation)"  
            References="@(Reference)"  
            DebugType="$(debuggingType)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).dll" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
        <Output TaskParameter="BuildSucceeded"  
                  PropertyName="BuildWorked" />  
    </Csc>  
</Target>  
```  
  
## Voir aussi  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)   
 [Tasks](../msbuild/msbuild-tasks.md)