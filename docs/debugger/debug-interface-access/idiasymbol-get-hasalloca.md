---
title: IDiaSymbol::get_hasAlloca | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasAlloca method
ms.assetid: 3b9fb747-670b-4da7-bb70-612f7b911786
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f86eb2c4e0d95d3fbb9c24ee8596193b31223b11
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56698389"
---
# <a name="idiasymbolgethasalloca"></a>IDiaSymbol::get_hasAlloca
Récupère un indicateur qui spécifie si la fonction contient un appel à `alloca` (qui est utilisé pour allouer de la mémoire sur la pile).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT get_hasAlloca(   BOOL *pFlag);
```

#### <a name="parameters"></a>Paramètres
 `pFlag`

[out] Retourne `TRUE` si la fonction contient un appel à `alloca`; sinon, retourne `FALSE`.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="requirements"></a>Spécifications

|Spécification|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK 8.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)