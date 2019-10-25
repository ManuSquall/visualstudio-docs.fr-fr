---
title: IDiaSymbol::findInlineFramesByVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 54295d3e-bbb6-4c10-ab9d-adcfc22b1f71
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f2ec0280f7eab6d5dd44c4577cfde2cd3846e5fd
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741139"
---
# <a name="idiasymbolfindinlineframesbyva"></a>IDiaSymbol::findInlineFramesByVA
Récupère une énumération qui permet à un client d’itérer au sein de tous les frames insérés sur une adresse virtuelle spécifiée (VA).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findInlineFramesByVA ( 
   ULONGLONG         va,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Paramètres
 `va`

dans Spécifie l’adresse en tant que VA.

 `ppResult`

à Contient un objet `IDiaEnumSymbols` qui contient la liste des frames récupérés.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; Sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)