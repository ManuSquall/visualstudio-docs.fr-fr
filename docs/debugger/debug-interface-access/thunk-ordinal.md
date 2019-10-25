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
ms.openlocfilehash: 1de2d6c9700dcb7b1106c3693d855bb1d8ae2cfa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738495"
---
# <a name="thunk_ordinal"></a>THUNK_ORDINAL
Désigne les types de thunks.

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
Thunk THUNK_ORDINAL_NOTYPE standard.

THUNK_ORDINAL_ADJUSTOR un thunk de réglage `this`.

Thunk d’appel virtuel THUNK_ORDINAL_VCALL.

THUNK_ORDINAL_PCODE P-code thunk.

Thunk de chargement différé THUNK_ORDINAL_LOAD.

THUNK_ORDINAL_TRAMP_INCREMENTAL incrémentielle trampoline thunk (un thunk trampoline est utilisé pour rebondir les appels d’un espace mémoire à un autre).

Thunk THUNK_ORDINAL_TRAMP_BRANCHISLAND Branch point trampoline.

## <a name="remarks"></a>Notes
Les valeurs de cette énumération sont retournées à partir d’un appel à la méthode [IDiaSymbol :: get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) .

## <a name="requirements"></a>spécifications
En-tête : cvconst. h

## <a name="see-also"></a>Voir aussi
- [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
