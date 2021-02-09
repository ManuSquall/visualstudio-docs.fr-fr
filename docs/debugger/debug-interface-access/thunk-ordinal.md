---
title: THUNK_ORDINAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3c3984f106b3b29a25adac70745166878927a60b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862275"
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
THUNK_ORDINAL_NOTYPE thunk standard.

THUNK_ORDINAL_ADJUSTOR un `this` thunk de réglage.

THUNK_ORDINAL_VCALL le thunk d’appel virtuel.

THUNK_ORDINAL_PCODE le thunk de code P.

THUNK_ORDINAL_LOAD le thunk de chargement différé.

THUNK_ORDINAL_TRAMP_INCREMENTAL thunk trampoline incrémentiel (un thunk trampoline est utilisé pour rebondir les appels d’un espace mémoire à un autre).

THUNK_ORDINAL_TRAMP_BRANCHISLAND thunk point de branche trampoline.

## <a name="remarks"></a>Remarques
Les valeurs de cette énumération sont retournées à partir d’un appel à la méthode [IDiaSymbol :: get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) .

## <a name="requirements"></a>Configuration requise
En-tête : cvconst. h

## <a name="see-also"></a>Voir aussi
- [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
