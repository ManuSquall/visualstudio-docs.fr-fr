---
title: When, élément (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#When
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <When> Element [MSBuild]
- When Element [MSBuild]
ms.assetid: eb27de6f-4e71-4e87-87e2-d93f7bf5899c
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fbbd0c6f697363ea4fab4b927ac36371b6f70fea
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49277162"
---
# <a name="when-element-msbuild"></a>When, élément (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Spécifie un bloc de code que l’élément `Choose` peut sélectionner.  
  
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
<When Condition="'StringA'=='StringB'">  
    <PropertyGroup>... </PropertyGroup>  
    <ItemGroup>... </ItemGroup>  
    <Choose>... </Choose>  
</When>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|Condition|Attribut requis.<br /><br /> Condition à évaluer. Pour plus d’informations, consultez l’article [Conditions (Conditions MSBuild)](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[Choose](../msbuild/choose-element-msbuild.md)|Élément facultatif.<br /><br /> Évalue les éléments enfants pour sélectionner une section de code à exécuter. Un élément `Choose` peut ne contenir aucun élément `When` ou en contenir plusieurs.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Élément facultatif.<br /><br /> Contient un ensemble d’éléments [Item](../msbuild/item-element-msbuild.md) définis par l’utilisateur. Un élément `ItemGroup` peut ne contenir aucun élément `When` ou en contenir plusieurs.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Élément facultatif.<br /><br /> Contient un ensemble d’éléments [Property](../msbuild/property-element-msbuild.md) définis par l’utilisateur. Un élément `When` peut ne contenir aucun élément `PropertyGroup` ou en contenir plusieurs.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Choose, élément (MSBuild)](../msbuild/choose-element-msbuild.md)|Évalue les éléments enfants pour sélectionner une section de code à exécuter.|  
  
## <a name="remarks"></a>Notes  
 Si l’attribut `Condition` s’évalue à true, les éléments `ItemGroup` et `PropertyGroup` enfants de l’élément `When` sont exécutés et tous les éléments `When` suivants sont ignorés.  
  
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



