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
ms.openlocfilehash: 19776c8d4ef72149c575d6835e9265e9cdb33727
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62855131"
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
Spécifie le type de mémoire à accéder.

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
`MemTypeCode` Accède à du code uniquement mémoire.

`MemTypeData` Accède aux données ou pile de mémoire.

`MemTypeStack` Accès uniquement mémoire de la pile.

`MemTypeAny` Accède à n’importe quel type de mémoire.

## <a name="remarks"></a>Notes
Les valeurs dans cette énumération sont transmises à la [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) méthode pour limiter l’accès à différents types de mémoire.

## <a name="requirements"></a>Configuration requise
En-tête : cvconst.h

## <a name="see-also"></a>Voir aussi
- [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)
