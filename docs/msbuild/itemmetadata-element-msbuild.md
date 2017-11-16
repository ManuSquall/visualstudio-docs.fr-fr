---
title: "Élément ItemMetadata (MSBuild) | Microsoft Docs"
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemMetadata Element [MSBuild]
- <ItemMetadata> Element [MSBuild]
ms.assetid: e3db5122-202d-43a9-b2f4-3e0ec4ed3d08
caps.latest.revision: "17"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: c48e85d299ed55de9eee286ca0f7a853cc4c669e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="itemmetadata-element-msbuild"></a>ItemMetadata, élément (MSBuild)
Contient une clé de métadonnées d’élément définie par l’utilisateur, qui contient la valeur des métadonnées de l’élément. Un élément peut comporter un nombre quelconque de paires clé-valeur de métadonnées.  

 \<Project>  
 \<ItemGroup>  
 \<Item>  

## <a name="syntax"></a>Syntaxe  

```  
<ItemMetadataName> Item Metadata value</ItemMetadataName>  
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
|[Item](../msbuild/item-element-msbuild.md)|Élément défini par l’utilisateur qui définit les entrées pour le processus de génération.|  

## <a name="text-value"></a>Valeur texte  
 Une valeur texte est facultative.  

 Ce texte spécifie la valeur des métadonnées de l’élément (texte ou XML).  

## <a name="remarks"></a>Notes  

## <a name="example"></a>Exemple  
 L’exemple de code ci-après indique comment ajouter des métadonnées `Culture` avec la valeur `fr` à l’élément `CSFile`.  

```xml  
<ItemGroup>  
    <CSFile Include="main.cs" >  
        <Culture>fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  

## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur le schéma de fichier projet MSBuild](../msbuild/msbuild-project-file-schema-reference.md)   
 [Éléments MSBuild](../msbuild/msbuild-items.md)
