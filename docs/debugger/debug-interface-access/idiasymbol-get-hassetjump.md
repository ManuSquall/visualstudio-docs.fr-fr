---
title: IDiaSymbol::get_hasSetJump | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasSetJump method
ms.assetid: 22656206-dccf-40ed-b179-fc016d1b262a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 353247c494b803871a9c64126545e11be39bfcae
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85463637"
---
# <a name="idiasymbolget_hassetjump"></a>IDiaSymbol::get_hasSetJump
Récupère un indicateur qui spécifie si la fonction contient une utilisation de la commande [setjmp](/cpp/c-runtime-library/reference/setjmp) (associée à la commande [longjmp](/cpp/c-runtime-library/reference/longjmp) , qui constituent la méthode de gestion des exceptions de style C).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_hasSetJump(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Paramètres
 `pFlag`

à Retourne `TRUE` si la fonction contient une `setjmp` commande ; sinon, retourne `FALSE` .

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
- [IDiaSymbol::get_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)
- [longjmp](/cpp/c-runtime-library/reference/longjmp)
- [setjmp](/cpp/c-runtime-library/reference/setjmp)