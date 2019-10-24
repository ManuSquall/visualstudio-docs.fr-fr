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
ms.openlocfilehash: 6ffd349b56c4292de04d5d7a38e82eeafed6775e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739468"
---
# <a name="idiasymbolget_registerid"></a>IDiaSymbol::get_registerId
Récupère l’indicateur de registre de l’emplacement lorsque l' [énumération LocationType (](../../debugger/debug-interface-access/locationtype.md) a la valeur `LocIsEnregistered`.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_registerId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne l’indicateur de registre de l’emplacement.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour de `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Notes
 Si le symbole est relatif à un registre, autrement dit, si l' [énumération LocationType (](../../debugger/debug-interface-access/locationtype.md) du symbole est définie sur `LocIsRegRel`, utilisez la méthode `get_registerId` suivie d’un appel à la méthode [IDiaSymbol :: get_Offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) pour obtenir le décalage à partir du registre où le symbole est trouvées.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md)