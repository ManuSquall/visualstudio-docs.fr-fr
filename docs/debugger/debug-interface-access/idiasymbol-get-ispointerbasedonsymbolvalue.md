---
title: IDiaSymbol::get_isPointerBasedOnSymbolValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 577c8011-9269-4373-8577-b4822a983724
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a7e7546454ddb60babff757f86aab023ce5bb7d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740141"
---
# <a name="idiasymbolget_ispointerbasedonsymbolvalue"></a>IDiaSymbol::get_isPointerBasedOnSymbolValue
Spécifie si le pointeur de `this` est basé sur une valeur de symbole.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_isPointerBasedOnSymbolValue(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Pointeur vers une `BOOL` qui spécifie si le pointeur `this` est basé sur une valeur de symbole.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne `S_FALSE` ou un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)