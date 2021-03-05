---
description: Les moteurs de débogage n’implémentent pas cette méthode.
title: 'IDebugThread2 :: GetLogicalThread | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9193cde20ba1035552451143c676aab291d7c684
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168346"
---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
Les moteurs de débogage n’implémentent pas cette méthode.

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
dans Objet [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) qui représente le frame de pile.

`ppLogicalThread`\
à Retourne une `IDebugLogicalThread2` interface qui représente le thread logique associé. Une implémentation du moteur de débogage doit définir cette valeur sur une valeur null.

## <a name="return-value"></a>Valeur renvoyée
 Les implémentations du moteur de débogage retournent toujours `E_NOTIMPL` .

## <a name="see-also"></a>Voir aussi
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
