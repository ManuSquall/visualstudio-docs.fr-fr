---
title: Élément Property (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Property> Element [MSBuild]
- Property Element [MSBuild]
ms.assetid: 69ab08ab-3e76-41dd-a01b-49aa1d2e0cac
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 739e39bd09e8387904570d3690e7c9ff1447fae3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53864441"
---
# <a name="property-element-msbuild"></a>Élément Property (MSBuild)
Contient une valeur et un nom de propriété définis par l’utilisateur. Chaque propriété utilisée dans un projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] doit être spécifiée en tant qu’enfant d’un élément `PropertyGroup`.  

 \<Project>  
 \<PropertyGroup >  

## <a name="syntax"></a>Syntaxe  

```xml  
<Property Condition="'String A' == 'String B'">  
    Property Value  
</Property>  
```  

## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  

### <a name="attributes"></a>Attributs  

|Attribut|Description|  
|---------------|-----------------|  
|`Condition`|Attribut facultatif.<br /><br /> Condition à évaluer. Pour plus d’informations, consultez l’article [Conditions (Conditions MSBuild)](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Éléments enfants  
 Aucun.  

### <a name="parent-elements"></a>Éléments parents  

|Élément|Description|  
|-------------|-----------------|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Élément grouping pour des propriétés.|  

## <a name="text-value"></a>Valeur texte  
 Une valeur texte est facultative.  

 Ce texte spécifie la valeur de propriété et peut contenir du code XML.  

## <a name="remarks"></a>Notes  
 Les noms de propriétés sont limités uniquement aux caractères ASCII. Les valeurs de propriété sont référencées dans le projet en plaçant le nom de propriété entre « `$(` » et « `)` ». Par exemple, `$(builddir)\classes` serait résolu en *build\classes* si la propriété `builddir` avait la valeur `build`. Pour plus d’informations sur les propriétés, voir [Propriétés MSBuild](../msbuild/msbuild-properties.md).  

## <a name="example"></a>Exemple  
 Le code suivant définit la propriété `Optimization` sur `false` et la propriété `DefaultVersion` sur `1.0` si la propriété `Version` est vide.  

```xml  
<PropertyGroup>  
    <Optimization>false</Optimization>  
    <DefaultVersion Condition="'$(Version)' == ''" >1.0</DefaultVersion>  
</PropertyGroup>  
```  

## <a name="see-also"></a>Voir aussi
[Propriétés MSBuild](../msbuild/msbuild-properties.md)  
 [Informations de référence sur le schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)
