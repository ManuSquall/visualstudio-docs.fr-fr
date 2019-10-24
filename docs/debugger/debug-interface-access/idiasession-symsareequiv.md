---
title: IDiaSession::symsAreEquiv | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 61cfc582f11670af8c956c3334681284ce5172a6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741870"
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

## <a name="return-value"></a>Valeur de retour
 Si les symboles sont équivalents, retourne `S_OK` ; Sinon, retourne `S_FALSE`, les symboles ne sont pas équivalents. Sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)