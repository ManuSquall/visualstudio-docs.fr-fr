---
title: Élément Property (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Property> Element [MSBuild]
- Property Element [MSBuild]
ms.assetid: 69ab08ab-3e76-41dd-a01b-49aa1d2e0cac
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a8b9ebd5207b4fc4a6274090b91e8fa3ab0b20cb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49262994"
---
# <a name="property-element-msbuild"></a>Property, élément (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Contient une valeur et un nom de propriété définis par l’utilisateur. Chaque propriété utilisée dans un projet [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] doit être spécifiée en tant qu’enfant d’un élément `PropertyGroup`.  
  
 \<Project>  
 \<PropertyGroup >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 Les noms de propriétés sont limités uniquement aux caractères ASCII. Les valeurs de propriété sont référencées dans le projet en plaçant le nom de propriété entre « `$(` » et « `)` ». Par exemple, `$(builddir)\classes` serait résolu en « build\classes » si la propriété `builddir` avait la valeur `build`. Pour plus d’informations sur les propriétés, consultez l’article [Propriétés MSBuild](msbuild-properties1.md).  
  
## <a name="example"></a>Exemple  
 Le code suivant définit la propriété `Optimization` sur `false` et la propriété `DefaultVersion` sur `1.0` si la propriété `Version` est vide.  
  
```  
<PropertyGroup>  
    <Optimization>false</Optimization>  
    <DefaultVersion Condition="'$(Version)' == ''" >1.0</DefaultVersion>  
</PropertyGroup>  
```  
  
## <a name="see-also"></a>Voir aussi
[Propriétés MSBuild](msbuild-properties1.md)  
 [Référence du schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)



