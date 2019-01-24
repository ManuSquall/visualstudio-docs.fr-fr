---
title: Opérateurs logiques et opérateurs avancés dans les expressions de recherche (Help Viewer)
ms.date: 11/02/2017
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Help Viewer, logical operators in search
- logical operators in search [Help Viewer]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b5e9739ffe1e66186f62bb87ef5ffabdef27801a
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "54406107"
---
# <a name="logical-and-advanced-operators-in-search-expressions"></a>Opérateurs logiques et opérateurs avancés dans les expressions de recherche

Vous pouvez utiliser des opérateurs logiques et des opérateurs de recherche avancés pour affiner votre recherche de contenu dans **Help Viewer**.

## <a name="logical-operators"></a>Opérateurs logiques

Les opérateurs logiques spécifient comment plusieurs termes de recherche doivent être combinés dans une requête de recherche. Le tableau suivant montre les opérateurs logiques AND, OR, NOT et NEAR.

|Pour rechercher|Utilisez|Exemple|Résultat|
|-------------------|---------|-------------|------------|
|Les deux termes dans le même article|AND|dib AND palette|Rubriques qui contiennent « dib » et « palette ».|
|L’un des deux termes dans un article|OU|trame OR vecteur|Rubriques qui contiennent « trame » ou « vecteur ».|
|Le premier terme sans le second terme dans le même article|NOT|« système d’exploitation » NOT DOS|Rubriques qui contiennent « système d’exploitation » mais pas « DOS ».|
|Les deux termes, proches, dans un article|NEAR|utilisateur NEAR noyau|Rubriques qui contiennent « utilisateur » à proximité de « noyau ».|

> [!IMPORTANT]
> Vous devez entrer les opérateurs logiques tout en majuscules pour que le moteur de recherche puisse les reconnaître.

## <a name="advanced-operators"></a>Opérateurs avancés

Les opérateurs de recherche avancés permettent d’affiner la recherche de contenu en spécifiant à quel endroit rechercher un terme dans un article. Le tableau suivant décrit les quatre opérateurs de recherche avancés disponibles.

|Pour rechercher|Utilisez|Exemple|Résultat|
|-------------------|---------|-------------|------------|
|Un terme dans le titre de l’article|`title:`|`title:binaryreader`|Rubriques qui contiennent « binaryreader » dans leur titre.|
|Un terme dans un exemple de code|`code:`|`code:readdouble`|Rubriques qui contiennent « readdouble » dans un exemple de code.|
|Un terme dans un exemple de langage de programmation spécifique|`code:vb:`|`code:vb:string`|Rubriques dans lesquelles un exemple de code Visual Basic contient « string ».|
|Un article qui est associé à un mot clé d’index spécifique|`keyword:`|`keyword:readbyte`|Rubriques associées au mot clé d’index « readbyte ».|

> [!IMPORTANT]
> Vous devez entrer les opérateurs de recherche avancée avec un signe deux-points final et sans espace avant ce signe pour que le moteur de recherche les identifie.

### <a name="programming-languages-for-code-examples"></a>Langages de programmation des exemples de code

Vous pouvez utiliser l’opérateur `code:` pour rechercher du contenu sur l’un des langages de programmation. Si vous voulez retourner des exemples pour un langage de programmation spécifique, utilisez l’une des valeurs de langage de programmation suivantes :

|Langage de programmation|Syntaxe de l’opérateur de recherche|
| - |---------|
|Visual Basic|`code:vb`<br/>`code:visualbasic`|
|C#|`code:c#`<br/>`code:csharp`|
|C++|`code:cpp`<br/>`code:c++`<br/>`code:cplusplus`|
|F#|`code:f#`<br/>`code:fsharp`|
|JavaScript|`code:javascript`<br/>`code:js`|
|XAML|`code:xaml`|

> [!NOTE]
> L’opérateur `code:` trouve uniquement le contenu qui est marqué à l’aide d’une étiquette de langage de programmation, contrairement au contenu qui est marqué génériquement comme du code.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour rechercher des rubriques](../help-viewer/find-topics.md)
- [Microsoft Help Viewer](../help-viewer/overview.md)
