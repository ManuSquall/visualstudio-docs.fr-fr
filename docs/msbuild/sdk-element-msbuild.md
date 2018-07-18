---
title: Élément Sdk (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 01/25/2018
ms.technology: msbuild
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6e22233d58cdb02194b5d5efe21bc397e9ae3a9c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
ms.locfileid: "31568043"
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
