---
title: "MSBuild Conditional Constructs | Microsoft Docs"
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
  - "<Choose> Element [MSBuild]"
  - "Choose Element [MSBuild]"
  - "conditional constructs [MSBuild]"
  - "MSBuild, conditional constructs"
  - "<When> Element [MSBuild]"
  - "<Otherwise> Element [MSBuild]"
  - "Otherwise Element [MSBuild]"
  - "When Element [MSBuild]"
ms.assetid: dd54258e-f4fb-448f-9da4-d1817e0cbaf2
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# MSBuild Conditional Constructs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] fournit un mécanisme pour le traitement either\/or à l'aide des éléments [Choose](../msbuild/choose-element-msbuild.md), [When](../msbuild/when-element-msbuild.md) et [Otherwise](../msbuild/otherwise-element-msbuild.md).  
  
## Utilisation de l'élément Choose  
 L'élément `Choose` contient une série d'éléments `When` avec les attributs `Condition` testés dans l'ordre de haut en bas jusqu'à ce que l'un d'entre eux ait la valeur `true`.  Si plusieurs éléments `When` ont la valeur `true`, seul le premier est utilisé.  S'il existe, l'élément `Otherwise` sera analysé si aucune condition d'un élément `When` n'a la valeur `true`.  
  
 Les éléments `Choose` peuvent être utilisés comme les éléments enfants des éléments `Project`, `When` et `Otherwise`.  Les éléments `When` et `Otherwise` peuvent avoir des éléments enfants `ItemGroup`, `PropertyGroup` ou `Choose`.  
  
## Exemple  
 L'exemple suivant utilise les éléments `Choose` et `When` pour le traitement de type inclusif\/exclusif.  Les propriétés et les éléments du projet sont définis en fonction de la valeur de la propriété `Configuration`.  
  
```  
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
  
## Voir aussi  
 [Choose Element \(MSBuild\)](../msbuild/choose-element-msbuild.md)   
 [When Element \(MSBuild\)](../msbuild/when-element-msbuild.md)   
 [Otherwise Element \(MSBuild\)](../msbuild/otherwise-element-msbuild.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)