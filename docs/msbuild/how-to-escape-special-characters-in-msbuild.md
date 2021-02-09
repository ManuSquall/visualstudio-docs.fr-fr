---
title: 'Comment : utiliser des caractères spéciaux d’échappement dans MSBuild | Microsoft Docs'
description: Découvrez comment échapper des caractères spéciaux afin de pouvoir utiliser ces caractères en tant que littéraux dans les fichiers projet MSBuild.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 44e4e713bf8f796f31fcca69a9451a77d120bcfc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914352"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Guide pratique pour utiliser des caractères spéciaux d’échappement dans MSBuild

Certains caractères ont une signification spéciale dans les fichiers projet MSBuild. Il s’agit par exemple des points-virgules (`;`) et des astérisques (`*`). Pour obtenir la liste complète de ces caractères spéciaux, consultez [caractères spéciaux MSBuild](../msbuild/msbuild-special-characters.md).

Pour pouvoir utiliser ces caractères spéciaux comme littéraux dans un fichier projet, vous devez les spécifier suivant la syntaxe `%<xx>`, où `<xx>` représente la valeur hexadécimale ASCII du caractère.

## <a name="msbuild-special-characters"></a>Caractères spéciaux MSBuild

Par exemple, les caractères spéciaux sont utilisés dans l’attribut `Include` des listes d’éléments. Par exemple, la liste d’éléments suivante déclare deux éléments : *MyFile.cs* et *MyClass.cs*.

```xml
<Compile Include="MyFile.cs;MyClass.cs"/>
```

Si vous souhaitez déclarer un élément qui contient un point-virgule dans le nom, vous devez utiliser la `%<xx>` syntaxe pour échapper le point-virgule et empêcher MSBuild de déclarer deux éléments distincts. Par exemple, l’élément suivant insère le point-virgule dans une séquence d’échappement et déclare un élément nommé `MyFile.cs;MyClass.cs`.

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
- [Éléments](../msbuild/msbuild-items.md)
