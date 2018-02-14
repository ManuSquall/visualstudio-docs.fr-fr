---
title: "Élément ImportGroup | Microsoft Docs"
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
- <ImportGroup> element [MSBuild]
- ImportGroup element [MSBuild]
ms.assetid: dac3fa2d-6678-4017-af35-93686f53f302
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 567df29941439a760d1537906a3d22d22db9f7e9
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="importgroup-element"></a>Élément ImportGroup
Contient une collection d’éléments `Import` regroupés sous une condition facultative. Pour plus d’informations, consultez [Import, élément (MSBuild)](../msbuild/import-element-msbuild.md).  

 \<Project>  
 \<ImportGroup>  

## <a name="syntax"></a>Syntaxe  

```  
<ImportGroup Condition="'String A' == 'String B'">  
    <Import ... />  
    <Import ... />  
</ImportGroup>  
```  

## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  

### <a name="attributes"></a>Attributs  

|Attribut|Description|  
|---------------|-----------------|  
|`Condition`|Attribut facultatif.<br /><br /> Condition à évaluer. Pour plus d’informations, consultez l’article [Conditions (Conditions MSBuild)](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Éléments enfants  

|Élément|Description|  
|-------------|-----------------|  
|[Import](../msbuild/import-element-msbuild.md)|Importe le contenu d’un fichier projet dans un autre fichier projet.|  

### <a name="parent-elements"></a>Éléments parents  

|Élément|Description|  
|-------------|-----------------|  
|[Projet](../msbuild/project-element-msbuild.md)|Élément racine requis d'un fichier projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] .|  

## <a name="remarks"></a>Notes  

## <a name="example"></a>Exemple  
 L’exemple de code suivant illustre l’élément `ImportGroup`.  

```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ImportGroup>  
        <Import Project="$(Targets1.targets) />  
        <Import Project="$(Targets2.targets) />  
    </ImportGroup>  
...  
</Project>  
```  

## <a name="see-also"></a>Voir aussi  
 [Référence du schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)   
 [Éléments](../msbuild/msbuild-items.md)
