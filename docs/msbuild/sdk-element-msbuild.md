---
title: "Élément Sdk (MSBuild) | Microsoft Docs"
ms.custom: 
ms.date: 01/25/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Sdk element [MSBuild]
- <Sdk> element [MSBuild]
author: jeffkl
ms.author: jeffkl
manager: angerlic
ms.workload:
- multiple
ms.openlocfilehash: 34db4807b3ab373c2a5b3c32fd9ef310263c3f7c
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2018
---
# <a name="sdk-element-msbuild"></a>Élément Sdk (MSBuild)
Référence un kit SDK de projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  

 \<Project>  
 \<Sdk>  


## <a name="syntax"></a>Syntaxe  

```  
<Sdk Name="My.Custom.Sdk"
     Version="1.0.0" />  
```  

## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  

### <a name="attributes"></a>Attributs  

|Attribut|Description|  
|---------------|-----------------|  
|`Name`|Attribut requis.<br /><br /> Nom du kit SDK de projet.|  
|`Version`|Attribut facultatif.<br /><br /> Version du kit SDK de projet.|  

### <a name="child-elements"></a>Éléments enfants  
 Aucun.

### <a name="parent-elements"></a>Éléments parents  
 |Élément|Description|  
|-------------|-----------------|  
|[Projet](../msbuild/project-element-msbuild.md)|Élément racine requis d'un fichier projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] .|  

## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour référencer un kit SDK de projet MSBuild](../msbuild/how-to-use-project-sdk.md)   
 [Référence du schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)   
 [MSBuild](../msbuild/msbuild.md)
