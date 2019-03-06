---
title: IDiaSymbol::get_offset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_offset method
ms.assetid: 8292bb08-4dc8-4663-beb4-258f5d5a448d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a85062b2012f44e8a3d7ff2356f8c053bc28ef7
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56638242"
---
# <a name="idiasymbolgetoffset"></a>IDiaSymbol::get_offset
Récupère le décalage de l’emplacement du symbole. Quand utiliser le [LocationType (énumération)](../../debugger/debug-interface-access/locationtype.md) est `LocIsRegRel` ou `LocIsBitField`.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_offset ( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

[out] Retourne le décalage en octets de l’emplacement du symbole.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Remarques
 Le décalage est d’un point connu précédemment déterminé. Par exemple, l’offset pour un `LocIsBitField` type d’emplacement est généralement à partir du début de la classe conteneur.

## <a name="requirements"></a>Spécifications

|Spécification|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK v7.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md)