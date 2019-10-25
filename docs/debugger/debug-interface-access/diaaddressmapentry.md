---
title: DiaAddressMapEntry | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 54b326116b1e1b677a997b264cf0c168a93febb0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745266"
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
`rva` une adresse virtuelle relative (RVA) dans l’image A.

`rvaTo` l’adresse virtuelle relative `rva` est mappée à dans l’image B.

## <a name="remarks"></a>Notes
Une carte d’adresses fournit une traduction d’une disposition d’image (A) à une autre (B). Tableau de `DiaAddressMapEntry` structures triées par `rva` définit un mappage d’adresses.

Pour traduire une adresse, `addrA`, dans l’image A en adresse, `addrB`, dans l’image B, procédez comme suit :

1. Recherchez l’entrée dans la carte, `e`, avec la plus grande `rva` inférieure ou égale à `addrA`.

2. Définir `delta = addrA - e.rva`.

3. Définir `addrB = e.rvaTo + delta`.

    Un tableau de structures de `DiaAddressMapEntry` est passé à la méthode [IDiaAddressMap :: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) .

## <a name="requirements"></a>spécifications
En-tête : Dia2. h

## <a name="see-also"></a>Voir aussi
- [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
