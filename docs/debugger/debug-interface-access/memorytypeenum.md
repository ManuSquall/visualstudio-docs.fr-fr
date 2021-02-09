---
title: MemoryTypeEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a92cc41fd0e6898ad0d108204f5b472000b9b65c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862310"
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
`MemTypeCode` Accède uniquement à la mémoire de code.

`MemTypeData` Accède à des données ou à la mémoire de pile.

`MemTypeStack` Accède uniquement à la mémoire de pile.

`MemTypeAny` Accède à n’importe quel type de mémoire.

## <a name="remarks"></a>Remarques
Les valeurs de cette énumération sont passées à la méthode [IDiaStackWalkHelper :: ReadMemory (](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) pour limiter l’accès à différents types de mémoire.

## <a name="requirements"></a>Configuration requise
En-tête : cvconst. h

## <a name="see-also"></a>Voir aussi
- [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)
