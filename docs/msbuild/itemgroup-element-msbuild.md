---
title: "&#201;l&#233;ment ItemGroup (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#ItemGroup"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "ItemGroup, élément [MSBuild]"
  - "<ItemGroup>, élément [MSBuild]"
ms.assetid: aac894e3-a9f1-4bbc-a796-6ef07001f35b
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# &#201;l&#233;ment ItemGroup (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contient un ensemble d'éléments [Item](../msbuild/item-element-msbuild.md) définis par l'utilisateur.  Chaque élément utilisé dans un projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] doit être spécifié en tant qu'enfant d'un élément `ItemGroup`.  
  
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
|[Élément](../msbuild/item-element-msbuild.md)|Définit les entrées pour le processus de génération.  Un élément `ItemGroup` peut contenir zéro, un ou plusieurs éléments `Item`.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Projet](../msbuild/project-element-msbuild.md)|Élément racine requis d'un fichier projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
|[Cible](../msbuild/target-element-msbuild.md)|Si vous démarrez le .NET Framework 3.5, l'élément `ItemGroup` peut s'afficher à l'intérieur d'un élément `Target`.  Pour plus d'informations, consultez [Targets](../msbuild/msbuild-targets.md).|  
  
## Notes  
  
## Exemple  
 L'exemple de code suivant illustre les collections d'éléments définies par l'utilisateur `Res` et `CodeFiles`, déclarées dans un élément `ItemGroup`.  Chaque élément de la collection `Res` contient un élément [ItemMetadata](../msbuild/itemmetadata-element-msbuild.md) enfant défini par l'utilisateur.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Res Include = "Strings.fr.resources" >  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include = "Dialogs.fr.resources" >  
            <Culture>fr</Culture>  
        </Res>  
  
        <CodeFiles Include="**\*.cs" Exclude="**\generated\*.cs" />  
        <CodeFiles Include="..\..\Resources\Constants.cs" />  
    </ItemGroup>  
...  
</Project>  
```  
  
## Voir aussi  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)   
 [Items](../msbuild/msbuild-items.md)   
 [Common MSBuild Project Items](../msbuild/common-msbuild-project-items.md)