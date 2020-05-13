---
title: BP_LOCATION_DATA_STRING Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 75f881feaaa2068abd98d771a63024f20435d98f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737972"
---
# <a name="bp_location_data_string"></a>BP_LOCATION_DATA_STRING
Utilisé pour définir des points de rupture de données qui sont basés sur une chaîne que l’utilisateur peut entrer à partir de l’environnement de développement intégré (IDE).

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
[L’objet IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) qui représente le fil sur lequel le point d’arrêt se produit.

`bstrContext`\
Le contexte du point d’arrêt dans le code, généralement une méthode ou un nom de fonction vu sur une pile d’appels.

`bstrDataExpr`\
La chaîne de données que l’utilisateur entre pour définir le point d’arrêt.

`dwNumElements`\
Le nombre d’éléments dans la chaîne de données dans lequel le point d’arrêt se produit.

## <a name="remarks"></a>Notes
Cette structure est membre de la structure [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) dans le cadre d’un syndicat.

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
