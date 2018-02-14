---
title: "Élément ItemMetadata (MSBuild) | Microsoft Docs"
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
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
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 6d74c2aa1e7364ae8138f491c3469734e12f5aee
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
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
 [Référence du schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)   
 [Éléments](../msbuild/msbuild-items.md)
