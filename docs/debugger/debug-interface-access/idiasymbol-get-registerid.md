---
title: IDiaSymbol::get_registerId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 19da4fdea411901af72c5be2f159964632d68558
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56611579"
---
# <a name="idiasymbolgetregisterid"></a>IDiaSymbol::get_registerId
Récupère l’indicateur de Registre de l’emplacement lorsque le [LocationType (énumération)](../../debugger/debug-interface-access/locationtype.md) est défini sur `LocIsEnregistered`.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_registerId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

[out] Retourne l’indicateur de Registre de l’emplacement.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Remarques
 Si le symbole est relatif à un Registre, autrement dit, si le symbole [LocationType (énumération)](../../debugger/debug-interface-access/locationtype.md) a la valeur `LocIsRegRel`, utiliser le `get_registerId` méthode suivie par un appel à la [IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) méthode pour obtenir le décalage à partir du Registre où se trouve le symbole.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md)