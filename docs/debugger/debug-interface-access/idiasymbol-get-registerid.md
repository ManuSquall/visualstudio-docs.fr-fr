---
description: Récupère l’indicateur de registre de l’emplacement lorsque l’énumération LocationType (est définie sur LocIsEnregistered'.
title: IDiaSymbol::get_registerId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3f6845c83b46fb524221933eb859742ebe7a95e6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161899"
---
# <a name="idiasymbolget_registerid"></a>IDiaSymbol::get_registerId
Récupère l’indicateur de registre de l’emplacement lorsque l' [énumération LocationType (](../../debugger/debug-interface-access/locationtype.md) a la valeur `LocIsEnregistered` .

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_registerId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne l’indicateur de registre de l’emplacement.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Notes
 Si le symbole est relatif à un registre, autrement dit, si l' [énumération LocationType (](../../debugger/debug-interface-access/locationtype.md) du symbole est définie sur `LocIsRegRel` , utilisez la `get_registerId` méthode suivie d’un appel à la méthode [IDiaSymbol :: get_Offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) pour obtenir le décalage à partir du registre où se trouve le symbole.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md)
