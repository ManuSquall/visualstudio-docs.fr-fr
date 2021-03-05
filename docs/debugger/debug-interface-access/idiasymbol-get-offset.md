---
description: Récupère le décalage de l’emplacement du symbole.
title: IDiaSymbol::get_offset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_offset method
ms.assetid: 8292bb08-4dc8-4663-beb4-258f5d5a448d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8c5c3e59596fdfc1e769710f8459620303e72d6a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155900"
---
# <a name="idiasymbolget_offset"></a>IDiaSymbol::get_offset
Récupère le décalage de l’emplacement du symbole. Utilisez lorsque l' [énumération LocationType (](../../debugger/debug-interface-access/locationtype.md) est `LocIsRegRel` ou `LocIsBitField` .

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_offset ( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne le décalage en octets de l’emplacement du symbole.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Notes
 Le décalage provient d’un point connu précédemment déterminé. Par exemple, le décalage d’un `LocIsBitField` type d’emplacement est généralement à partir du début de la classe conteneur.

## <a name="requirements"></a>Configuration requise

|Condition requise|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK v 7.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md)
