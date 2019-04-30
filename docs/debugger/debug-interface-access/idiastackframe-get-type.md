---
title: IDiaStackFrame::get_type | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_type method
ms.assetid: 99daa97b-5c05-455d-bd1e-800762ccf7c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa4478788c820485ac3284e9533987ceb8e3492f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62832116"
---
# <a name="idiastackframegettype"></a>IDiaStackFrame::get_type
Récupère le type de trame.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_type ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

[out] Retourne une valeur de la [StackFrameTypeEnum (énumération)](../../debugger/debug-interface-access/stackframetypeenum.md) énumération.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si la propriété n’est pas pris en charge. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [StackFrameTypeEnum, énumération](../../debugger/debug-interface-access/stackframetypeenum.md)