---
title: Élément Sdk (MSBuild) | Microsoft Docs
ms.date: 01/25/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40b155af29d2d81a43eb0270e776e40df335a4bf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62838774"
---
# <a name="sdk-element-msbuild"></a>Élément Sdk (MSBuild)
Référence un kit SDK de projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].

 \<Project> \<Sdk>

## <a name="syntax"></a>Syntaxe

```xml
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

| Élément | Description |
| - | - |
| [Projet](../msbuild/project-element-msbuild.md) | Élément racine requis d'un fichier projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] . |

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour référencer un kit SDK de projet MSBuild](../msbuild/how-to-use-project-sdk.md)
- [Informations de référence sur le schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
