---
title: Choose, élément (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Choose
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Choose> Element [MSBuild]
- Choose Element [MSBuild]
ms.assetid: 7b8b025a-d944-4f5c-9018-c89fc2ef146d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 642a4996b9b7cb24ead5b58e8f3f98b8abf7657c
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59650614"
---
# <a name="choose-element-msbuild"></a>Choose, élément (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Évalue des éléments enfants pour sélectionner un ensemble d’éléments `ItemGroup` et/ou d’éléments `PropertyGroup` à évaluer.  
  
 \<Project>  
 \<Choose>  
 \<When>  
 \<Choose>  
 ...  
 \<Otherwise>  
 \<Choose>  
 ...  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|[Otherwise](../msbuild/otherwise-element-msbuild.md)|Élément facultatif.<br /><br /> Spécifie le bloc de code `PropertyGroup` et les éléments `ItemGroup` à exécuter si les conditions de tous les éléments `When` correspondent à la valeur `false`. Un élément `Choose` peut ne contenir aucun élément `Otherwise` ou en contenir un seul qui doit figurer en dernière position.|  
|[When](../msbuild/when-element-msbuild.md)|Élément requis.<br /><br /> Spécifie un bloc de code que l’élément `Choose` peut sélectionner. Un élément `Choose` peut contenir un ou plusieurs éléments `When`.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Otherwise](../msbuild/otherwise-element-msbuild.md)|Spécifie le bloc de code à exécuter si les conditions de tous les éléments `When` correspondent à la valeur `false`.|  
|[Projet](../msbuild/project-element-msbuild.md)|Élément racine requis d'un fichier projet [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .|  
|[When](../msbuild/when-element-msbuild.md)|Spécifie un bloc de code que l’élément `Choose` peut sélectionner.|  
  
## <a name="remarks"></a>Remarques  
 Les éléments `Choose`, `When` et `Otherwise` sont utilisés ensemble pour permettre la sélection d’une section de code spécifique à exécuter parmi plusieurs options possibles. Pour plus d’informations, consultez [Constructions conditionnelles](../msbuild/msbuild-conditional-constructs.md).  
  
## <a name="example"></a>Exemple  
 Le projet suivant utilise l’élément `Choose` pour sélectionner l’ensemble de valeurs de propriété à définir dans les éléments `When`. Si les attributs `Condition` des deux éléments `When` s’évaluent à `false`, les valeurs des propriétés dans l’élément `Otherwise` sont définies.  
  
```  
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
 [Constructions conditionnelles MSBuild](../msbuild/msbuild-conditional-constructs.md)   
 [Référence du schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)
