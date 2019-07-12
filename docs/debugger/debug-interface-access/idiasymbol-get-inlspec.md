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
ms.openlocfilehash: 8860668452a22413db8c6fc3d0fdc664c7ba36dd
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "64835390"
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
> La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="requirements"></a>Configuration requise

|Prérequis|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK 8.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [inline, __inline, \__forceinline](/cpp/cpp/inline-functions-cpp)