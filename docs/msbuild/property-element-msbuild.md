---
title: Élément Property (MSBuild) | Microsoft Docs
description: En savoir plus sur l’élément de propriété MSBuild, qui contient un nom et une valeur de propriété définis par l’utilisateur qui doivent être spécifiés en tant qu’enfant d’un élément PropertyGroup.
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 617a6d3712b137d76334d4063f36a1b8dde1d101
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918844"
---
# <a name="property-element-msbuild"></a>Élément Property (MSBuild)

Contient une valeur et un nom de propriété définis par l’utilisateur. Chaque propriété utilisée dans un projet MSBuild doit être spécifiée en tant qu’enfant d’un `PropertyGroup` élément.

 \<Project> \<PropertyGroup>

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

 Les noms de propriétés sont limités uniquement aux caractères ASCII. Les valeurs de propriété sont référencées dans le projet en plaçant le nom de propriété entre « `$(` » et « `)` ». Par exemple, `$(builddir)\classes` est résolu en *build\classes*, si la `builddir` propriété avait la valeur `build` . Pour plus d’informations sur les propriétés, consultez [propriétés MSBuild](../msbuild/msbuild-properties.md).

## <a name="example"></a>Exemple

 Le code suivant définit la propriété `Optimization` sur `false` et la propriété `DefaultVersion` sur `1.0` si la propriété `Version` est vide.

```xml
<PropertyGroup>
    <Optimization>false</Optimization>
    <DefaultVersion Condition="'$(Version)' == ''" >1.0</DefaultVersion>
</PropertyGroup>
```

## <a name="see-also"></a>Voir aussi

- [MSBuild (propriétés)](../msbuild/msbuild-properties.md)
- [Référence du schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)
