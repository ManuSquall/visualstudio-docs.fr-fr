---
title: Constructions conditionnelles MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0ade8344b5f4189e9588fc8e75ef88fa5cf8f8c5
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080195"
---
# <a name="msbuild-conditional-constructs"></a>Constructions conditionnelles MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] fournit un mécanisme de traitement de type « soit/soit » avec les éléments [Choose](../msbuild/choose-element-msbuild.md), [When](../msbuild/when-element-msbuild.md) et [Otherwise](../msbuild/otherwise-element-msbuild.md).  
  
## <a name="use-the-choose-element"></a>Utiliser l’élément Choose  
 L’élément `Choose` contient une série d’éléments `When` avec des attributs `Condition` qui sont testés du haut vers le bas, jusqu’à ce qu’un élément avec la valeur `true` soit trouvé. Si plusieurs éléments `When` ont la valeur `true`, seul le premier est utilisé. Un élément `Otherwise` (si présent) est évalué si aucune condition d’un élément `When` n’a la valeur `true`.  
  
 Les éléments `Choose` peuvent être utilisés comme des éléments enfants des éléments `Project`, `When` et `Otherwise`. Les éléments `When` et `Otherwise` peuvent avoir des éléments enfants `ItemGroup`, `PropertyGroup` ou `Choose`.  
  
## <a name="example"></a>Exemple  
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
 [Choose, élément (MSBuild)](../msbuild/choose-element-msbuild.md)   
 [When, élément (MSBuild)](../msbuild/when-element-msbuild.md)   
 [Otherwise, élément (MSBuild)](../msbuild/otherwise-element-msbuild.md)   
 [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)