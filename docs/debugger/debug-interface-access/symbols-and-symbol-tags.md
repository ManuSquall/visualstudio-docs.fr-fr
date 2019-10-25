---
title: Symboles et balises de symboles | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d2281a82926dabfde88b8d4bb9096f0e9624211
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738529"
---
# <a name="symbols-and-symbol-tags"></a>Balises Symbols et Symbol
Les informations de débogage relatives à un programme compilé sont stockées dans le fichier de base de données du programme (. pdb) sous forme de symboles accessibles à l’aide des API du kit de développement logiciel (SDK) debug interface Access (DIA). Tous les symboles ont un [IDiaSymbol :: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) et une propriété [IDiaSymbol :: get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) . La propriété `symTag` indique le type de symbole tel que défini par l’énumération d' [énumération SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) . La propriété `symIndexId` est une valeur `DWORD` qui contient l’identificateur unique pour chaque instance d’un symbole.

 Les symboles ont également des propriétés qui peuvent spécifier des informations supplémentaires sur le symbole ainsi que des références à d’autres symboles, le plus souvent un [IDiaSymbol :: get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) ou [IDiaSymbol :: get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). Lorsque vous interrogez une propriété qui contient une référence, la référence est retournée en tant qu’objet [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) . Ces propriétés sont toujours associées à une autre propriété du même nom, mais avec le suffixe « ID », par exemple, [IDiaSymbol :: get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) et [IDiaSymbol :: get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md). Les tables dans les [emplacements de symboles](../../debugger/debug-interface-access/symbol-locations.md), la [hiérarchie lexicale des types de symboles](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)et la [hiérarchie de classes des types de symboles](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) présentent les propriétés de chacun des différents genres de symboles. Ces propriétés peuvent contenir des informations pertinentes sur les autres symboles ou des références à d’autres symboles. Étant donné que les propriétés de `*Id` sont simplement des identificateurs ordinaux numériques de leurs propriétés connexes, elles sont omises des discussions supplémentaires. Ils sont référencés uniquement là où cela est nécessaire pour clarifier les paramètres.

 Quand vous tentez d’accéder à la propriété, si aucune erreur ne se produit et qu’une valeur a été assignée à la propriété Symbol, la méthode « obtenir » de la propriété retourne `S_OK`. Une valeur de retour de `S_FALSE` indique que la propriété n’est pas valide pour le symbole actuel.

## <a name="in-this-section"></a>Dans cette section

[Emplacements des symboles](../../debugger/debug-interface-access/symbol-locations.md)

Décrit les différents types d’emplacements qu’un symbole peut avoir.

[Hiérarchie lexicale des types de symboles](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)

Décrit les types de symboles qui forment des hiérarchies lexicales telles que des fichiers, des modules et des fonctions.

[Hiérarchie de classes des types de symboles](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)

Décrit les types de symboles qui correspondent à des éléments de langage différents tels que les classes, les tableaux et les types de retour de fonction.

## <a name="see-also"></a>Voir aussi

- [SDK Debug Interface Access](../../debugger/debug-interface-access/debug-interface-access-sdk.md)