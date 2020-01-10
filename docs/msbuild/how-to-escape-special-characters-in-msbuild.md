---
title: 'Comment : utiliser des caractères spéciaux d’échappement dans MSBuild | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- special characters, escaping
- characters, escapes
- escape characters
- MSBuild, escaping special characters
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 955739372605b9e4f9fe58f73669322e2724de31
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595005"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Guide pratique pour utiliser des caractères spéciaux d’échappement dans MSBuild

Certains caractères ont une signification spéciale dans les fichiers projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Il s’agit par exemple des points-virgules (`;`) et des astérisques (`*`). Pour obtenir la liste complète de ces caractères spéciaux, consultez [Caractères spéciaux MSBuild](../msbuild/msbuild-special-characters.md).

Pour pouvoir utiliser ces caractères spéciaux comme littéraux dans un fichier projet, vous devez les spécifier suivant la syntaxe `%<xx>`, où `<xx>` représente la valeur hexadécimale ASCII du caractère.

## <a name="msbuild-special-characters"></a>Caractères spéciaux MSBuild

Par exemple, les caractères spéciaux sont utilisés dans l’attribut `Include` des listes d’éléments. Par exemple, la liste d’éléments suivante déclare deux éléments : *MyFile.cs* et *MyClass.cs*.

```xml
<Compile Include="MyFile.cs;MyClass.cs"/>
```

Si vous souhaitez déclarer un élément dont le nom comporte un point-virgule, vous devez utiliser la syntaxe `%<xx>` pour insérer ce point-virgule dans une séquence d’échappement et empêcher [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] de déclarer deux éléments distincts. Par exemple, l’élément suivant insère le point-virgule dans une séquence d’échappement et déclare un élément nommé `MyFile.cs;MyClass.cs`.

```xml
<Compile Include="MyFile.cs%3BMyClass.cs"/>
```

Vous pouvez également utiliser une [fonction de propriété](../msbuild/property-functions.md) pour insérer des chaînes dans une séquence d’échappement. Par exemple, ceci est équivalent à l’exemple ci-dessus.

```xml
<Compile Include="$([MSBuild]::Escape('MyFile.cs;MyClass.cs'))" />
```

### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>Pour utiliser un caractère spécial MSBuild comme caractère littéral

Utilisez la notation `%<xx>` à la place du caractère spécial, où `<xx>` représente la valeur hexadécimale du caractère ASCII. Par exemple, pour utiliser un astérisque (`*`) comme caractère littéral, utilisez la valeur `%2A`.

## <a name="see-also"></a>Voir aussi
- [Concepts MSBuild](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Éléments MSBuild](../msbuild/msbuild-items.md)
