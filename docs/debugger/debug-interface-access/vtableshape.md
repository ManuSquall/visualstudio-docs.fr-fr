---
title: VTableShape | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- VTableShape symbol
- SymTagVTableShape tag
ms.assetid: dd97f4c3-115d-46a9-b506-2531e30a0d8f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d4a21f07d4fd4fe055ebee4d6c7d5cd1faed0a3b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56616324"
---
# <a name="vtableshape"></a>VTableShape
Le [VTable](../../debugger/debug-interface-access/vtable.md) symbole possède un symbole d’enfants de classe identifié par le `SymTagVTableShape` balise.

## <a name="properties"></a>Propriétés
 Le tableau suivant montre des propriétés supplémentaires valides pour ce type de symbole.

|Property|Type de données|Description|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` Si la classe de VTable est marquée en tant que constante.|
|[IDiaSymbol::get_count](../../debugger/debug-interface-access/idiasymbol-get-count.md)|`DWORD`|Nombre d’entrées dans la VTable.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbole de la compiland englobant.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID du symbole lexicale parente.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID d’index de symbole.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Retourne `SymTagVTableShape` (parmi les [SymTagEnum (énumération)](../../debugger/debug-interface-access/symtagenum.md) valeurs).|
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` Si la classe de VTable n’est pas alignée.|
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` Si la classe de VTable est marquée comme volatile.|

## <a name="see-also"></a>Voir aussi
- [Hiérarchie de classes des types de symboles](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)
- [VTable](../../debugger/debug-interface-access/vtable.md)