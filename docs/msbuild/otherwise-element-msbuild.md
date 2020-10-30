---
title: Otherwise, élément (MSBuild) | Microsoft Docs
description: Découvrez comment MSBuild utilise l’élément otherwise pour spécifier le bloc de code à exécuter si et seulement si les conditions de All sont false.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Otherwise
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Otherwise> Element [MSBuild]
- Otherwise Element [MSBuild]
ms.assetid: de3997e9-1595-4263-a886-95530b56a319
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05cc8820f073ea8c620e4331c180ee1ddbfc2b65
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048935"
---
# <a name="otherwise-element-msbuild"></a>Élément Otherwise (MSBuild)

Spécifie le bloc de code à exécuter si et seulement si les conditions de tous les éléments `When` correspondent à la valeur `false`.

 \<Project> \<Choose>
 \<When>
 \<Choose>
... \<Otherwise>
 \<Choose>
...

## <a name="syntax"></a>Syntax

```xml
<Otherwise>
    <PropertyGroup>... </PropertyGroup>
    <ItemGroup>... </ItemGroup>
    <Choose>... </Choose>
</Otherwise>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

 Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Choisissez](../msbuild/choose-element-msbuild.md)|Élément facultatif.<br /><br /> Évalue les éléments enfants pour sélectionner une section de code à exécuter. Un élément `Otherwise` peut ne contenir aucun élément `Choose` ou en contenir plusieurs.|
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Élément facultatif.<br /><br /> Contient un ensemble d’éléments [Item](../msbuild/item-element-msbuild.md) définis par l’utilisateur. Un élément `Otherwise` peut ne contenir aucun élément `ItemGroup` ou en contenir plusieurs.|
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Élément facultatif.<br /><br /> Contient un ensemble d’éléments [Property](../msbuild/property-element-msbuild.md) définis par l’utilisateur. Un élément `Otherwise` peut ne contenir aucun élément `PropertyGroup` ou en contenir plusieurs.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Choisissez](../msbuild/choose-element-msbuild.md)|Évalue les éléments enfants pour sélectionner une section de code à exécuter.|

## <a name="remarks"></a>Remarques

 Un élément `Choose` ne peut comprendre qu’un seul élément `Otherwise` qui doit figurer en dernière position.

 Les éléments `Choose`, `When` et `Otherwise` sont utilisés ensemble pour permettre la sélection d’une section de code spécifique à exécuter parmi plusieurs options possibles. Pour plus d’informations, consultez [Constructions conditionnelles](../msbuild/msbuild-conditional-constructs.md).

## <a name="example"></a>Exemple

 Le projet suivant utilise l’élément `Choose` pour sélectionner l’ensemble de valeurs de propriété à définir dans les éléments `When`. Si les attributs `Condition` des deux éléments `When` s’évaluent à `false`, les valeurs des propriétés dans l’élément `Otherwise` sont définies.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <PropertyGroup>
        <Configuration Condition="'$(Configuration)' == ''">Debug</Configuration>
        <OutputType>Exe</OutputType>
        <RootNamespace>ConsoleApplication1</RootNamespace>
        <AssemblyName>ConsoleApplication1</AssemblyName>
        <WarningLevel>4</WarningLevel>
    </PropertyGroup>
    <Choose>
        <When Condition=" '$(Configuration)'=='debug' ">
            <PropertyGroup>
                <DebugSymbols>true</DebugSymbols>
                <DebugType>full</DebugType>
                <Optimize>false</Optimize>
                <OutputPath>.\bin\Debug\</OutputPath>
                <DefineConstants>DEBUG;TRACE</DefineConstants>
            </PropertyGroup>
            <ItemGroup>
                <Compile Include="UnitTesting\*.cs" />
                <Reference Include="NUnit.dll" />
            </ItemGroup>
        </When>
        <When Condition=" '$(Configuration)'=='retail' ">
            <PropertyGroup>
                <DebugSymbols>false</DebugSymbols>
                <Optimize>true</Optimize>
                <OutputPath>.\bin\Release\</OutputPath>
                <DefineConstants>TRACE</DefineConstants>
            </PropertyGroup>
        </When>
        <Otherwise>
            <PropertyGroup>
                <DebugSymbols>true</DebugSymbols>
                <Optimize>false</Optimize>
                <OutputPath>.\bin\$(Configuration)\</OutputPath>
                <DefineConstants>DEBUG;TRACE</DefineConstants>
            </PropertyGroup>
        </Otherwise>
        </Choose>
    <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
</Project>
```

## <a name="see-also"></a>Voir aussi

- [Constructions conditionnelles](../msbuild/msbuild-conditional-constructs.md)
- [Référence du schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)
