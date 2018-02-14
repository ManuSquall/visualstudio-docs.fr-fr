---
title: "Élément PropertyGroup (MSBuild) | Microsoft Docs"
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#PropertyGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <PropertyGroup> element [MSBuild]
- PropertyGroup element [MSBuild]
ms.assetid: ff1e6c68-b9a1-4263-a1ce-dc3b829a64d4
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e19722c1da702684200d848eb62d1dd46a900590
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="propertygroup-element-msbuild"></a>PropertyGroup, élément (MSBuild)
Contient un ensemble d’éléments [Property](../msbuild/property-element-msbuild.md) définis par l’utilisateur. Chaque élément `Property` utilisé dans un projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] doit être un enfant d’un élément `PropertyGroup`.  

 \<Project>  
 \<PropertyGroup >  

## <a name="syntax"></a>Syntaxe  

```  
<PropertyGroup Condition="'String A' == 'String B'">  
    <Property1>...</Property1>  
    <Property2>...</Property2>  
</PropertyGroup>  
```  

## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  

### <a name="attributes"></a>Attributs  

|Attribut|Description|  
|---------------|-----------------|  
|Condition|Attribut facultatif.<br /><br /> Condition à évaluer. Pour plus d’informations, consultez l’article [Conditions (Conditions MSBuild)](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Éléments enfants  

|Élément|Description|  
|-------------|-----------------|  
|[Property](../msbuild/property-element-msbuild.md)|Élément facultatif.<br /><br /> Nom de propriété défini par l’utilisateur, qui contient la valeur de propriété. Un élément `PropertyGroup` peut ne contenir aucun élément *Property* ou en contenir plusieurs.|  

### <a name="parent-elements"></a>Éléments parents  

|Élément|Description|  
|-------------|-----------------|  
|[Projet](../msbuild/project-element-msbuild.md)|Élément racine requis d'un fichier projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] .|  

## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment définir des propriétés en fonction d’une condition. Dans cet exemple, si la valeur de la propriété `CompileConfig` est `DEBUG`, les propriétés `Optimization`, `Obfuscate` et `OutputPath` contenues dans l’élément `PropertyGroup` sont définies.  

```xml  
<PropertyGroup Condition="'$(CompileConfig)' == 'DEBUG'" >  
    <Optimization>false</Optimization>  
    <Obfuscate>false</Obfuscate>  
    <OutputPath>$(OutputPath)\debug</OutputPath>  
</PropertyGroup>  
```  

## <a name="see-also"></a>Voir aussi  
 [Référence du schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)  
 [Propriétés MSBuild](../msbuild/msbuild-properties.md)
