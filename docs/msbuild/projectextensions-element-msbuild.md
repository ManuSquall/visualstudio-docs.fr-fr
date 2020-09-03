---
title: Élément ProjectExtensions (MSBuild) | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94f2d88aa19bf01ebe6f25c7d80772c812abcc59
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77632964"
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

## <a name="remarks"></a>Notes

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
