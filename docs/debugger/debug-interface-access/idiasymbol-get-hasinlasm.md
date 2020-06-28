---
title: IDiaSymbol::get_hasInlAsm | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasInlAsm method
ms.assetid: 7001c7cc-1459-4929-851b-a08066a803c6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8bd9207a802a919e1dd86624584bda6963d2f278
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85463707"
---
# <a name="idiasymbolget_hasinlasm"></a>IDiaSymbol::get_hasInlAsm
Récupère un indicateur qui spécifie si la fonction contient un assembly inline.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_hasInlAsm(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Paramètres
 `pFlag`

à Retourne `TRUE` si la fonction a un assembly inline ; sinon, retourne `FALSE` .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="requirements"></a>Configuration requise

|Condition requise|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK v 8.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)