---
title: IDiaSymbol::get_hasSEH | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasSEH method
ms.assetid: 1a709ded-22c8-464c-97be-eba5e464210c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0f9e7b1dc2fb5a338dc2cd2edbf3cf9d0eb2441
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85463665"
---
# <a name="idiasymbolget_hasseh"></a>IDiaSymbol::get_hasSEH
Récupère un indicateur qui spécifie si la fonction contient une [gestion structurée des exceptions (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp) (par exemple, des blocs __try/ \_ _except).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_hasSEH(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Paramètres
 `pFlag`

à Retourne `TRUE` si la fonction contient des blocs de gestion structurée des exceptions ; sinon, retourne `FALSE` .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou code d’erreur.

> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="requirements"></a>Configuration requise

|Condition requise|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK v 8.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Structured Exception Handling (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp)