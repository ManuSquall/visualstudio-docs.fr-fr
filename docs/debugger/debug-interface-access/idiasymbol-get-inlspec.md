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
ms.openlocfilehash: 5675239e35ab3bef809e3d54544d87d7a9e8bb75
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740379"
---
# <a name="idiasymbolget_inlspec"></a>IDiaSymbol::get_InlSpec
Cette fonction récupère un indicateur qui spécifie si la fonction a été marquée comme inline (à l’aide de l’un des attributs [inline,](/cpp/cpp/inline-functions-cpp) _ _ inline \__forceinline).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_inlSpec(
   BOOL *pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne `TRUE` si la fonction a été marquée comme Inline ; Sinon, retourne `FALSE`.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour de `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="requirements"></a>spécifications

|Exigence|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK v 8.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [inline, __inline, \__forceinline](/cpp/cpp/inline-functions-cpp)