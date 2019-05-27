---
title: IDebugThread2::GetLogicalThread | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d4273d1c8bff6f07fdcf12b5b324d8d42eb08799
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66199722"
---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
Moteurs de débogage n’implémentent pas cette méthode.

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
[in] Un [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) objet qui représente le frame de pile.

`ppLogicalThread`\
[out] Retourne un `IDebugLogicalThread2` interface qui représente le thread logique associé. Une implémentation du moteur de débogage doit lui affecter la valeur null.

## <a name="return-value"></a>Valeur de retour
 Déboguer des implémentations de moteur retournent toujours `E_NOTIMPL`.

## <a name="see-also"></a>Voir aussi
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)