---
title: Élément ItemDefinitionGroup (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ItemDefinitionGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemDefinitionGroup Element [MSBuild]
- <ItemDefinitionGroup> Element [MSBuild]
ms.assetid: 4e9fb04b-5148-4ae5-a394-42861dd62371
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b5aea9c7c7868dfdd9726b86bb344456ebe707d8
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59666986"
---
# <a name="itemdefinitiongroup-element-msbuild"></a>ItemDefinitionGroup, élément (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’élément `ItemDefinitionGroup` vous permet de définir un ensemble de définitions d’élément, correspondant à des valeurs de métadonnées appliquées par défaut à tous les éléments du projet. ItemDefinitionGroup évite d’avoir à utiliser les tâches [CreateItem](../msbuild/createitem-task.md) et [CreateProperty](../msbuild/createproperty-task.md). Pour plus d’informations, consultez l’article [Item Definitions (Définitions des éléments)](../msbuild/item-definitions.md).  
  
 \<Project>  
 \<ItemDefinitionGroup>  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<ItemGroup Condition="'String A' == 'String B'">  
    <Item1>... </Item1>  
    <Item2>... </Item2>  
</ItemGroup>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Condition`|Attribut facultatif. Condition à évaluer. Pour plus d’informations, consultez l’article [Conditions (Conditions MSBuild)](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[Item](../msbuild/item-element-msbuild.md)|Définit les entrées du processus de génération. Un élément `ItemDefinitionGroup` peut ne contenir aucun élément `Item` ou en contenir plusieurs.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Projet](../msbuild/project-element-msbuild.md)|Élément racine requis d'un fichier projet [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .|  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant définit deux éléments de métadonnées, m et n, dans un élément ItemDefinitionGroup. Dans cet exemple, les métadonnées par défaut « m » sont appliquées à l’élément « i », car les métadonnées « m » ne sont pas explicitement définies par l’élément « i ». Cependant, les métadonnées par défaut « n » ne sont pas appliquées à l’élément « i », car les métadonnées « n » sont déjà définies par l’élément « i ».  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemDefinitionGroup>  
        <i>  
            <m>m1</m>  
            <n>n1</n>  
        </i>        
    </ItemDefinitionGroup>  
    <ItemGroup>  
        <i Include="a">  
            <o>o1</o>  
            <n>n2</n>  
        </i>  
    </ItemGroup>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence du schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)   
 [Éléments](../msbuild/msbuild-items.md)
