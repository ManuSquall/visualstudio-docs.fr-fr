---
title: "ItemMetadata Element (MSBuild) | Microsoft Docs"
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
  - "ItemMetadata Element [MSBuild]"
  - "<ItemMetadata> Element [MSBuild]"
ms.assetid: e3db5122-202d-43a9-b2f4-3e0ec4ed3d08
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# ItemMetadata Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contient une clé des métadonnées de l'élément définie par l'utilisateur et contenant la valeur des métadonnées de l'élément.  Un élément peut avoir un nombre quelconque de paires clé\/valeur de métadonnées.  
  
## Syntaxe  
  
```  
<ItemMetadataName> Item Metadata value </ItemMetadataName>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Condition`|Attribut facultatif.<br /><br /> Condition à évaluer.  Pour plus d'informations, consultez [Conditions](../msbuild/msbuild-conditions.md).|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément](../msbuild/item-element-msbuild.md)|Élément défini par l'utilisateur qui définit les entrées pour le processus de génération.|  
  
## Valeur texte  
 Une valeur texte est facultative.  
  
 Ce texte spécifie la valeur des métadonnées de l'élément \(texte ou XML\).  
  
## Notes  
  
## Exemple  
 L'exemple de code suivant montre comment ajouter des métadonnées `Culture` avec la valeur `fr` à l'élément `CSFile`.  
  
```  
<ItemGroup>  
    <CSFile Include="main.cs" >  
        <Culture>fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
## Voir aussi  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)   
 [Items](../msbuild/msbuild-items.md)