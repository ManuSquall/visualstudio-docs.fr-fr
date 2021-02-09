---
title: BP_LOCATION_DATA_STRING | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: ce47dc9a3fac9ee56b801e4d2681668f4467f532
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902161"
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

## <a name="remarks"></a>Remarques
Cette structure est un membre de la structure [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) dans le cadre d’une Union.

## <a name="requirements"></a>Configuration requise
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
