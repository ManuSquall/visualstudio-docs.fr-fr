---
title: Opérateurs logiques dans les expressions de recherche (visionneuse d’aide)
ms.date: 11/02/2017
ms.topic: reference
helpviewer_keywords:
- Help Viewer, logical operators in search
- logical operators in search [Help Viewer]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a5d17d40a34835c1c8f99f4ad446de747771fa4a
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89741657"
---
# <a name="logical-and-advanced-operators-in-search-expressions"></a>Opérateurs logiques et opérateurs avancés dans les expressions de recherche

Vous pouvez utiliser des opérateurs logiques et des opérateurs de recherche avancés pour affiner votre recherche de contenu dans **Help Viewer**.

## <a name="logical-operators"></a>Opérateurs logiques

Les opérateurs logiques spécifient comment plusieurs termes de recherche doivent être combinés dans une requête de recherche. Le tableau suivant montre les opérateurs logiques AND, OR, NOT et NEAR.

|Pour rechercher|Utiliser|Exemple|Résultats|
|-------------------|---------|-------------|------------|
|Les deux termes dans le même article|AND|dib AND palette|Rubriques qui contiennent « dib » et « palette ».|
|L’un des deux termes dans un article|OR|trame OR vecteur|Rubriques qui contiennent « trame » ou « vecteur ».|
|Le premier terme sans le second terme dans le même article|NOT|« système d’exploitation » NOT DOS|Rubriques qui contiennent « système d’exploitation » mais pas « DOS ».|
|Les deux termes, proches, dans un article|NEAR|utilisateur NEAR noyau|Rubriques qui contiennent « utilisateur » à proximité de « noyau ».|

> [!IMPORTANT]
> Vous devez entrer les opérateurs logiques tout en majuscules pour que le moteur de recherche puisse les reconnaître.

## <a name="advanced-operators"></a>Opérateurs avancés

Les opérateurs de recherche avancés permettent d’affiner la recherche de contenu en spécifiant à quel endroit rechercher un terme dans un article. Le tableau suivant décrit les quatre opérateurs de recherche avancée disponibles.

|Pour rechercher|Utiliser|Exemple|Résultats|
|-------------------|---------|-------------|------------|
|Un terme dans le titre de l’article|`title:`|`title:binaryreader`|Rubriques qui contiennent « binaryreader » dans leur titre.|
|Un terme dans un exemple de code|`code:`|`code:readdouble`|Rubriques qui contiennent « readdouble » dans un exemple de code.|
|Un terme dans un exemple de langage de programmation spécifique|`code:vb:`|`code:vb:string`|Rubriques qui contiennent « string » dans un exemple de code Visual Basic.|
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

- [Comment : Rechercher des rubriques](../help-viewer/find-topics.md)
- [Microsoft Help Viewer](../help-viewer/overview.md)
