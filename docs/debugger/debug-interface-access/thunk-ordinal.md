---
title: THUNK_ORDINAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 776ee35e57b62463d47fc6f7fa26133f507f16f9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62854438"
---
# <a name="thunkordinal"></a>THUNK_ORDINAL
Désigne les types de conversion de code.

## <a name="syntax"></a>Syntaxe

```C++
typedef enum THUNK_ORDINAL {
    THUNK_ORDINAL_NOTYPE,
    THUNK_ORDINAL_ADJUSTOR,
    THUNK_ORDINAL_VCALL,
    THUNK_ORDINAL_PCODE,
    THUNK_ORDINAL_LOAD

    // trampoline thunk ordinals - only for use in Trampoline thunk symbols
    THUNK_ORDINAL_TRAMP_INCREMENTAL,
    THUNK_ORDINAL_TRAMP_BRANCHISLAND,
} THUNK_ORDINAL;
```

## <a name="elements"></a>Éléments
Conversion de code THUNK_ORDINAL_NOTYPE Standard.

THUNK_ORDINAL_ADJUSTOR A `this` thunk d’expert.

Conversion de code d’appel THUNK_ORDINAL_VCALL virtuel.

Thunk de P-code THUNK_ORDINAL_PCODE.

Conversion de code charge THUNK_ORDINAL_LOAD délai.

Thunk de trampoline THUNK_ORDINAL_TRAMP_INCREMENTAL incrémentielle (un thunk trampoline est utilisé pour retransmettre des appels à partir de l’espace mémoire d’un à un autre).

Thunk de trampoline THUNK_ORDINAL_TRAMP_BRANCHISLAND branche point.

## <a name="remarks"></a>Notes
Les valeurs dans cette énumération sont retournées à partir d’un appel à la [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) (méthode).

## <a name="requirements"></a>Configuration requise
En-tête : cvconst.h

## <a name="see-also"></a>Voir aussi
- [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
