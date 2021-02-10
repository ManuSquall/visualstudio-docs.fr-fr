---
title: Élément Sdk (MSBuild) | Microsoft Docs
description: En savoir plus sur la syntaxe, les attributs et les éléments de l’élément SDK MSBuild, qui fait référence à un kit de développement logiciel (SDK) de projet MSBuild.
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cd5f66cc6500a3320e0da962985f5b7fff1e86dc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937899"
---
# <a name="sdk-element-msbuild"></a>Élément Sdk (MSBuild)

Référence un kit de développement logiciel (SDK) de projet MSBuild.

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
| [Projet](../msbuild/project-element-msbuild.md) | Élément racine requis d’un fichier projet MSBuild. |

## <a name="see-also"></a>Voir aussi

- [Guide pratique : Faire référence à un kit SDK de projet MSBuild](../msbuild/how-to-use-project-sdk.md)
- [Référence du schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
