---
description: Utilisé pour définir des points d’arrêt sur variable basés sur une chaîne que l’utilisateur peut entrer à partir de l’environnement de développement intégré (IDE).
title: BP_LOCATION_DATA_STRING | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 98cfb12649fe85ce9e5f6b6a51a8c61243b5e9da
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096757"
---
# <a name="bp_location_data_string"></a>BP_LOCATION_DATA_STRING
Utilisé pour définir des points d’arrêt sur variable basés sur une chaîne que l’utilisateur peut entrer à partir de l’environnement de développement intégré (IDE).

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _BP_LOCATION_DATA_STRING {
    IDebugThread2* pThread;
    BSTR           bstrContext;
    BSTR           bstrDataExpr;
    DWORD          dwNumElements;
} BP_LOCATION_DATA_STRING;
```

## <a name="members"></a>Membres
`pThread`\
Objet [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) qui représente le thread sur lequel le point d’arrêt se produit.

`bstrContext`\
Contexte du point d’arrêt dans le code, généralement une méthode ou un nom de fonction tel qu’il apparaît sur une pile des appels.

`bstrDataExpr`\
Chaîne de données entrée par l’utilisateur pour définir le point d’arrêt.

`dwNumElements`\
Nombre d’éléments dans la chaîne de données dans laquelle le point d’arrêt se produit.

## <a name="remarks"></a>Notes
Cette structure est un membre de la structure [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) dans le cadre d’une Union.

## <a name="requirements"></a>Spécifications
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
