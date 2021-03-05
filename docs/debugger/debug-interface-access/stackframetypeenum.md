---
description: Spécifie le type de frame de pile.
title: StackFrameTypeEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b84ad19ec31cd1fae65913827b8ee381711f6534
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155305"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
Spécifie le type de frame de pile.

## <a name="syntax"></a>Syntaxe

```C++
enum StackFrameTypeEnum {
    FrameTypeFPO,
    FrameTypeTrap,
    FrameTypeTSS,
    FrameTypeStandard,
    FrameTypeFrameData,
    FrameTypeUnknown = -1
};
```

## <a name="elements"></a>Éléments
`FrameTypeFPO` Pointeur de frame omis ; Informations FPO disponibles.

`FrameTypeTrap` Trame d’interruption du noyau.

`FrameTypeTSS` Trame d’interruption du noyau.

`FrameTypeStandard` Frame de pile EBP standard.

`FrameTypeFrameData` Pointeur de frame omis ; Informations sur les données de frame disponibles.

`FrameTypeUnknown` Frame qui ne contient aucune information de débogage.

## <a name="remarks"></a>Notes
Les valeurs de cette énumération sont retournées par un appel à la méthode [IDiaStackFrame :: get_Type](../../debugger/debug-interface-access/idiastackframe-get-type.md) .

## <a name="requirements"></a>Configuration requise
En-tête : cvconst. h

## <a name="see-also"></a>Voir aussi
- [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)
