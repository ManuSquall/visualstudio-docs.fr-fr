---
title: IEnumDebugBoundBreakpoints2::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugBoundBreakpoints2::Next
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2::Next
ms.assetid: cb3a249f-2282-4bdc-b6d8-a4ee4bfb8365
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 92de3edb5e0720654714555f6073c19561450c3c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66314175"
---
# <a name="ienumdebugboundbreakpoints2next"></a>IEnumDebugBoundBreakpoints2::Next
Retourne l’ensemble suivant d’éléments de l’énumération.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Next(
   ULONG                    celt,
   IDebugBoundBreakpoint2** rgelt,
   ULONG*                   pceltFetched
);
```

```csharp
int Next(
   uint                     celt,
   IDebugBoundBreakpoint2[] rgelt,
   ref uint                 pceltFetched
);
```

## <a name="parameters"></a>Paramètres
`celt`\
[in] Le nombre d’éléments à récupérer. Spécifie également la taille maximale de la `rgelt` tableau.

`rgelt`\
[in, out] Tableau de [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) éléments doit être renseigné.

`pceltFetched`\
[out] Retourne le nombre d’éléments réellement retournés dans `rgelt`.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si inférieur au nombre demandé d’éléments peut être retournés ; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)