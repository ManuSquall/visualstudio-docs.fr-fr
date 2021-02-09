---
title: Élément ProjectExtensions (MSBuild) | Microsoft Docs
description: En savoir plus sur l’élément MSBuildProjectExtensions, qui permet aux fichiers projet MSBuild de contenir des informations non MSBuild.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ProjectExtensions
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ProjectExtensions> element [MSBuild]
- ProjectExtensions element [MSBuild]
ms.assetid: f95f312f-ff92-41eb-9469-ad99e236a307
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b7b186fa1d7a5ecb8297045d4b0bbb111d136d1d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905287"
---
# <a name="projectextensions-element-msbuild"></a>Élément ProjectExtensions (MSBuild)

Permet aux fichiers projet MSBuild de contenir des informations non MSBuild. Tout ce qui se trouve à l’intérieur d’un `ProjectExtensions` élément sera ignoré par MSBuild.

 \<Project> \<ProjectExtensions>

## <a name="syntax"></a>Syntaxe

```xml
<ProjectExtensions>
    Non-MSBuild information to include in file.
</ProjectExtensions>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

 None

### <a name="child-elements"></a>Éléments enfants

 None

### <a name="parent-elements"></a>Éléments parents

| Élément | Description |
| - | - |
| [Projet](../msbuild/project-element-msbuild.md) | Élément racine requis d’un fichier projet MSBuild. |

## <a name="remarks"></a>Remarques

 Un seul `ProjectExtensions` élément peut être utilisé dans un projet MSBuild.

## <a name="example"></a>Exemple

 L’exemple de code suivant affiche les informations de l’environnement de développement intégré stockées dans un élément `ProjectExtensions`.

```xml
<ProjectExtensions>
    <VSIDE>
        <External>
            <!--
            Raw XML passed to the IDE by an external source
            -->
        </External>
    </VSIDE>
</ProjectExtensions>
```

## <a name="see-also"></a>Voir aussi

- [Référence du schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
