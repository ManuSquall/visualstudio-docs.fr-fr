---
title: DiaAddressMapEntry | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 05475d2e6d48e7a8dacea834e5d7ca18c71d3260
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857306"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
Décrit une entrée dans une table d’adresses.

## <a name="syntax"></a>Syntaxe

```C++
struct DiaAddressMapEntry {
    DWORD rva,
    DWORD rvaTo
};
```

## <a name="elements"></a>Éléments
`rva` Une adresse virtuelle relative (RVA) dans l’image A.

`rvaTo` L’adresse virtuelle relative `rva` est mappée à dans l’image B.

## <a name="remarks"></a>Remarques
Une carte d’adresses fournit une traduction d’une disposition d’image (A) à une autre (B). Un tableau de `DiaAddressMapEntry` structures triées par `rva` définit un mappage d’adresses.

Pour traduire une adresse, `addrA` , dans l’image A en une adresse, `addrB` , dans l’image B, procédez comme suit :

1. Recherchez l’entrée dans la carte, `e` , avec la valeur la plus grande `rva` inférieure ou égale à `addrA` .

2. Définissez `delta = addrA - e.rva`.

3. Définissez `addrB = e.rvaTo + delta`.

    Un tableau de `DiaAddressMapEntry` structures est passé à la méthode [IDiaAddressMap :: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) .

## <a name="requirements"></a>Configuration requise
En-tête : Dia2. h

## <a name="see-also"></a>Voir aussi
- [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
