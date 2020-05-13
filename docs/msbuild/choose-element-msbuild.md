---
title: Choose, élément (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Choose
dev_langs:
- VB
- CSharp
- C++
- jsharp
- xml
helpviewer_keywords:
- <Choose> Element [MSBuild]
- Choose Element [MSBuild]
ms.assetid: 7b8b025a-d944-4f5c-9018-c89fc2ef146d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c4f699b4ffc9372af0c803d094390544932d652b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634472"
---
# <a name="choose-element-msbuild"></a>Choose, élément (MSBuild)

Évalue des éléments enfants pour sélectionner un ensemble d’éléments `ItemGroup` et/ou d’éléments `PropertyGroup` à évaluer.

 \<Projet> \<Choisissez> \<Quand> \<choisissez> ... \<Sinon,> \<choisissez> ...

## <a name="syntax"></a>Syntaxe

```xml
<Choose>
    <When Condition="'StringA'=='StringB'">... </When>
    <Otherwise>... </Otherwise>
</Choose>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

 Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[Sinon](../msbuild/otherwise-element-msbuild.md)|Élément facultatif.<br /><br /> Spécifie le bloc de code `PropertyGroup` et les éléments `ItemGroup` à exécuter si les conditions de tous les éléments `When` correspondent à la valeur `false`. Un élément `Choose` peut ne contenir aucun élément `Otherwise` ou en contenir un seul qui doit figurer en dernière position.|
|[Quand](../msbuild/when-element-msbuild.md)|Élément requis.<br /><br /> Spécifie un bloc de code que l’élément `Choose` peut sélectionner. Un élément `Choose` peut contenir un ou plusieurs éléments `When`.|

### <a name="parent-elements"></a>Éléments parents

| Élément | Description |
| - | - |
| [Sinon](../msbuild/otherwise-element-msbuild.md) | Spécifie le bloc de code à exécuter si les conditions de tous les éléments `When` correspondent à la valeur `false`. |
| [Projet](../msbuild/project-element-msbuild.md) | Élément racine requis d’un fichier de projet MSBuild. |
| [Quand](../msbuild/when-element-msbuild.md) | Spécifie un bloc de code que l’élément `Choose` peut sélectionner. |

## <a name="remarks"></a>Notes 

 Les éléments `Choose`, `When` et `Otherwise` sont utilisés ensemble pour permettre la sélection d’une section de code spécifique à exécuter parmi plusieurs options possibles. Pour plus d’informations, consultez [Constructions conditionnelles](../msbuild/msbuild-conditional-constructs.md).

## <a name="example"></a> Exemple

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
- [Référence du schéma de fichier de projet](../msbuild/msbuild-project-file-schema-reference.md)
