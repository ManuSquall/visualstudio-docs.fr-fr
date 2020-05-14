---
title: Constructions conditionnelles MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Choose> Element [MSBuild]
- Choose Element [MSBuild]
- conditional constructs [MSBuild]
- MSBuild, conditional constructs
- <When> Element [MSBuild]
- <Otherwise> Element [MSBuild]
- Otherwise Element [MSBuild]
- When Element [MSBuild]
ms.assetid: dd54258e-f4fb-448f-9da4-d1817e0cbaf2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0a06849c2aa0f4ec0203a7209ffc78be438dba9e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633380"
---
# <a name="msbuild-conditional-constructs"></a>Constructions conditionnelles MSBuild

MSBuild fournit un mécanisme pour l’un ou l’autre / ou le traitement avec le [Choisir](../msbuild/choose-element-msbuild.md), [Quand](../msbuild/when-element-msbuild.md), et [autrement](../msbuild/otherwise-element-msbuild.md) des éléments.

## <a name="use-the-choose-element"></a>Utiliser l’élément Choose

 L’élément `Choose` contient une série d’éléments `When` avec des attributs `Condition` qui sont testés du haut vers le bas, jusqu’à ce qu’un élément avec la valeur `true` soit trouvé. Si plusieurs éléments `When` ont la valeur `true`, seul le premier est utilisé. Un élément `Otherwise` (si présent) est évalué si aucune condition d’un élément `When` n’a la valeur `true`.

 Les éléments `Choose` peuvent être utilisés comme des éléments enfants des éléments `Project`, `When` et `Otherwise`. Les éléments `When` et `Otherwise` peuvent avoir des éléments enfants `ItemGroup`, `PropertyGroup` ou `Choose`.

## <a name="example"></a> Exemple

 L’exemple suivant utilise les éléments `Choose` et `When` pour un traitement de type « soit/soit ». Les propriétés et les éléments du projet sont définis en fonction de la valeur de la propriété `Configuration`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <OutputType>Exe</OutputType>
        <RootNamespace>ConsoleApplication1</RootNamespace>
        <AssemblyName>ConsoleApplication1</AssemblyName>
        <WarningLevel>4</WarningLevel>
    </PropertyGroup>
    <Choose>
        <When Condition=" '$(Configuration)'=='Debug' ">
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
    </Choose>
    <!-- Rest of Project -->
</Project>
```

## <a name="see-also"></a>Voir aussi

- [Choisissez l’élément (MSBuild)](../msbuild/choose-element-msbuild.md)
- [Lorsque l’élément (MSBuild)](../msbuild/when-element-msbuild.md)
- [Otherwise, élément (MSBuild)](../msbuild/otherwise-element-msbuild.md)
- [Référence MSBuild](../msbuild/msbuild-reference.md)
