---
title: UdtKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- UdtKind enumeration
ms.assetid: 400b59b9-373c-42cb-aae1-570494214328
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 44c543d09a360bfb7eadad11d7fca84764bb2006
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873393"
---
# <a name="udtkind"></a>UdtKind
Décrit la variété d’un type défini par l’utilisateur (UDT).

## <a name="syntax"></a>Syntaxe

```C++
enum UdtKind {
    UdtStruct,
    UdtClass,
    UdtUnion,
    UdtInterface
};
```

## <a name="elements"></a>Éléments
UdtStruct UDT est une structure.

UdtClass UDT est une classe.

UdtUnion UDT est une Union.

UdtInterface UDT est une interface.

## <a name="remarks"></a>Remarques
Les valeurs de cette énumération sont retournées par la méthode [IDiaSymbol :: get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md) .

## <a name="requirements"></a>Configuration requise
En-tête : cvconst. h

## <a name="see-also"></a>Voir aussi
- [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)
