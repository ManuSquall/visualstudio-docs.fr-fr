---
description: Indique si le symbole correspond à un symbole de fonction de niveau supérieur pour un nuanceur compilé pour un accélérateur qui correspond à un appel de parallel_for_each.
title: IDiaSymbol::get_isAcceleratorStubFunction | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: cc4ea375-76f6-4ba8-baed-c5fa82108137
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 710622fdb8fb10d0357c060097f13bab3be7d05f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156215"
---
# <a name="idiasymbolget_isacceleratorstubfunction"></a>IDiaSymbol::get_isAcceleratorStubFunction
Indique si le symbole correspond à un symbole de fonction de niveau supérieur pour un nuanceur compilé pour un accélérateur qui correspond à un `parallel_for_each` appel.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_isAcceleratorStubFunction(
   BOOL* pFlag);
```

#### <a name="parameters"></a>Paramètres
 `pFlag`

à Pointeur vers un `BOOL` qui indique si le symbole correspond à un symbole de fonction de niveau supérieur pour un nuanceur compilé pour un accélérateur qui correspond à un `parallel_for_each` appel.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
