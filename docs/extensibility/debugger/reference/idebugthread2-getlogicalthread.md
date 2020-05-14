---
title: IDebugThread2::GetLogicalThread ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e148fb0b9b043fc1717effca00d698ee14beb2f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718843"
---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
Les moteurs Debug ne mettent pas en œuvre cette méthode.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetLogicalThread( 
   IDebugStackFrame2*     pStackFrame,
   IDebugLogicalThread2** ppLogicalThread
);
```

```csharp
int GetLogicalThread( 
   IDebugStackFrame2        pStackFrame,
   out IDebugLogicalThread2 ppLogicalThread
);
```

## <a name="parameters"></a>Paramètres
`pStackFrame`\
[dans] Un objet [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) qui représente le cadre de pile.

`ppLogicalThread`\
[out] Retourne `IDebugLogicalThread2` une interface qui représente le thread logique associé. Une mise en œuvre du moteur de débogé devrait définir cette valeur nulle.

## <a name="return-value"></a>Valeur de retour
 Les implémentations `E_NOTIMPL`du moteur Debug reviennent toujours.

## <a name="see-also"></a>Voir aussi
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
