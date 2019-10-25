---
title: StackFrameTypeEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 20b0c9dd106e5744a369ddaa6cb870788f7464d3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738552"
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
pointeur de frame `FrameTypeFPO` omis ; Informations FPO disponibles.

`FrameTypeTrap` trame d’interruption du noyau.

`FrameTypeTSS` trame d’interruption du noyau.

`FrameTypeStandard` frame de pile EBP standard.

pointeur de frame `FrameTypeFrameData` omis ; Informations sur les données de frame disponibles.

Frame de `FrameTypeUnknown` qui ne contient aucune information de débogage.

## <a name="remarks"></a>Notes
Les valeurs de cette énumération sont retournées par un appel à la méthode [IDiaStackFrame :: get_Type](../../debugger/debug-interface-access/idiastackframe-get-type.md) .

## <a name="requirements"></a>spécifications
En-tête : cvconst. h

## <a name="see-also"></a>Voir aussi
- [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)
