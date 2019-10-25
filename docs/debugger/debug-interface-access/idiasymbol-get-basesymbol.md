---
title: IDiaSymbol::get_baseSymbol | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cabb5a18-bda7-47e8-9e46-5f4718579fc9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 307358522609659a8a95b94a0adf037026f5b948
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740942"
---
# <a name="idiasymbolget_basesymbol"></a>IDiaSymbol::get_baseSymbol
Récupère le symbole à partir duquel le pointeur est basé.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_baseSymbol(
   IDiaSymbol** pRetVal);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Pointeur vers le symbole à partir duquel le pointeur est basé.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne `S_FALSE` ou un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_baseSymbolId](../../debugger/debug-interface-access/idiasymbol-get-basesymbolid.md)