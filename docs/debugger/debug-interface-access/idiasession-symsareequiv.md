---
description: Vérifie si deux symboles sont équivalents.
title: IDiaSession::symsAreEquiv | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c5f887b13195bdde133c4bca845291b1255b99ea
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156985"
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
Vérifie si deux symboles sont équivalents.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT symsAreEquiv ( 
   IDiaSymbol* symbolA,
   IDiaSymbol* symbolB
);
```

#### <a name="parameters"></a>Paramètres
 `symbolA`

dans Premier objet [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) utilisé dans la comparaison.

 `symbolB`

dans Deuxième `IDiaSymbol` objet utilisé dans la comparaison.

## <a name="return-value"></a>Valeur renvoyée
 Si les symboles sont équivalents, retourne `S_OK` ; sinon, retourne `S_FALSE` , les symboles ne sont pas équivalents. Sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
