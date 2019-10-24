---
title: MemoryTypeEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0710ec5cdfcfcb59407d18b43b885603f017fdb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738628"
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
Spécifie le type de mémoire auquel accéder.

## <a name="syntax"></a>Syntaxe

```C++
enum MemoryTypeEnum {
    MemTypeCode,
    MemTypeData,
    MemTypeStack,
    MemTypeAny = -1
};
```

#### <a name="parameters"></a>Paramètres
`MemTypeCode` accède uniquement à la mémoire de code.

`MemTypeData` accède à des données ou à la mémoire de pile.

`MemTypeStack` accède uniquement à la mémoire de pile.

`MemTypeAny` accède à n’importe quel type de mémoire.

## <a name="remarks"></a>Notes
Les valeurs de cette énumération sont passées à la méthode [IDiaStackWalkHelper :: ReadMemory (](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) pour limiter l’accès à différents types de mémoire.

## <a name="requirements"></a>spécifications
En-tête : cvconst. h

## <a name="see-also"></a>Voir aussi
- [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)
