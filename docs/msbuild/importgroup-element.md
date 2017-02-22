---
title: "ImportGroup Element | Microsoft Docs"
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
  - "<ImportGroup> element [MSBuild]"
  - "ImportGroup element [MSBuild]"
ms.assetid: dac3fa2d-6678-4017-af35-93686f53f302
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# ImportGroup Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contient une collection d'éléments `Import` regroupés sous une condition facultative.  Pour plus d'informations, consultez [Import, élément \(MSBuild\)](../msbuild/import-element-msbuild.md).  
  
## Syntaxe  
  
```  
<ImportGroup Condition="'String A' == 'String B'">  
    <Import ... />  
    <Import ... />  
</ImportGroup>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Condition`|Attribut facultatif.<br /><br /> Condition à évaluer.  Pour plus d'informations, consultez [Conditions](../msbuild/msbuild-conditions.md).|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[Importer](../msbuild/import-element-msbuild.md)|Importe le contenu d'un fichier projet dans un autre fichier projet.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Projet](../msbuild/project-element-msbuild.md)|Élément racine requis d'un fichier projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
  
## Notes  
  
## Exemple  
 L'exemple de code suivant présente l'élément `ImportGroup`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ImportGroup>  
        <Import Project="$(Targets1.targets) />  
        <Import Project="$(Targets2.targets) />  
    </ImportGroup>  
...  
</Project>  
```  
  
## Voir aussi  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)   
 [Items](../msbuild/msbuild-items.md)