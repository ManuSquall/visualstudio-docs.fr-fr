---
title: "ItemDefinitionGroup Element (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#ItemDefinitionGroup"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "ItemDefinitionGroup Element [MSBuild]"
  - "<ItemDefinitionGroup> Element [MSBuild]"
ms.assetid: 4e9fb04b-5148-4ae5-a394-42861dd62371
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# ItemDefinitionGroup Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'élément  `ItemDefinitionGroup` vous permet de définir un jeu de définitions d'élément, qui sont des valeurs de métadonnées appliquées par défaut à tous les éléments dans le projet.  ItemDefinitionGroup remplace l'usage de [CreateItem Task](../msbuild/createitem-task.md) et [CreateProperty Task](../msbuild/createproperty-task.md).  Pour plus d'informations, consultez [Item Definitions](../msbuild/item-definitions.md).  
  
## Syntaxe  
  
```  
<ItemGroup Condition="'String A' == 'String B'">  
    <Item1>... </Item1>  
    <Item2>... </Item2>  
</ItemGroup>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Condition`|Attribut facultatif.  Condition à évaluer.  Pour plus d'informations, consultez [Conditions](../msbuild/msbuild-conditions.md).|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément](../msbuild/item-element-msbuild.md)|Définit les entrées pour le processus de génération.  Un élément `ItemDefinitionGroup` peut contenir zéro, un ou plusieurs éléments `Item`.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Projet](../msbuild/project-element-msbuild.md)|Élément racine requis d'un fichier projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
  
## Exemple  
 L'exemple de code suivant définit deux éléments de métadonnées, m et n, dans un ItemDefinitionGroup.  Dans cet exemple, la métadonnée par défaut "m" est appliquée à l'Élément "i" parce que la métadonnée "m" n'est pas explicitement définie par l'Élément "i".  Toutefois, la métadonnée par défaut "n" n'est pas appliquée à l'Élément "i" parce que la métadonnée "n" est déjà définie par l'Élément "i".  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemDefinitionGroup>  
        <i>  
            <m>m1</m>  
            <n>n1</n>  
        </i>        
    </ItemDefinitionGroup>  
    <ItemGroup>  
        <i Include="a">  
            <o>o1</o>  
            <n>n2</n>  
        </i>  
    </ItemGroup>  
    ...  
</Project>  
```  
  
## Voir aussi  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)   
 [Items](../msbuild/msbuild-items.md)