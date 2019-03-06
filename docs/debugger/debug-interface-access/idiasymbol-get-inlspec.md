---
title: IDiaSymbol::get_InlSpec | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_InlSpec method
ms.assetid: 30af6a2f-be84-429e-a96a-d0f9ed9343fb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b82196d2440c3bf5d5c5c24471bc094f8bc5b7b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56638203"
---
# <a name="idiasymbolgetinlspec"></a>IDiaSymbol::get_InlSpec
Cette fonction extrait un indicateur indiquant si la fonction a été marquée comme étant inline (à l’aide d’un de le [inline, __inline, \__forceinline](/cpp/cpp/inline-functions-cpp) attributs).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_inlSpec(
   BOOL *pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

[out] Retourne `TRUE` si la fonction a été marquée comme inline ; sinon, retourne `FALSE`.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou code d’erreur.

> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="requirements"></a>Spécifications

|Spécification|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK 8.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [inline, __inline, \__forceinline](/cpp/cpp/inline-functions-cpp)