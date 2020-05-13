---
title: IDebugErrorBreakpoint2::GetPendingBreakpoint (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpoint2::GetPendingBreakpoint
helpviewer_keywords:
- IDebugErrorBreakpoint2::GetPendingBreakpoint
ms.assetid: 59d0defc-99fd-445c-bdac-8224d5dea3f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0cdd84437d0f2480cacfd66860564b908ea76dd1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730143"
---
# <a name="idebugerrorbreakpoint2getpendingbreakpoint"></a>IDebugErrorBreakpoint2::GetPendingBreakpoint
Obtient le point d’arrêt en attente qui a causé l’erreur.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetPendingBreakpoint ( 
   IDebugPendingBreakpoint2** ppPendingBreakpoint
);
```

```csharp
int GetPendingBreakpoint ( 
   out IDebugPendingBreakpoint2 ppPendingBreakpoint
);
```

## <a name="parameters"></a>Paramètres
`ppPendingBreakpoint`\
[out] Retourne un objet [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) qui représente le point d’arrêt en attente qui n’a pas été lié.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
