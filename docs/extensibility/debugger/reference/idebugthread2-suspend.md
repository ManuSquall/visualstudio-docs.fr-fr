---
description: Interrompt un thread.
title: 'IDebugThread2 :: suspend | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 902418aeb18c149b0732e972a34ed89b56bb22ce
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081137"
---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
Interrompt un thread.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Suspend ( 
   DWORD *pdwSuspendCount
);
```

```csharp
HRESULT Suspend ( 
   out uint pdwSuspendCount
);
```

## <a name="parameters"></a>Paramètres
`pdwSuspendCount`\
à Retourne le nombre de suspensions après l’opération de suspension.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Chaque appel à cette méthode incrémente le nombre de suspensions au-dessus de 0. Ce nombre de suspensions s’affiche dans la fenêtre de débogage des **Threads** .

 Pour chaque appel à cette méthode, il doit y avoir un appel ultérieur à la méthode [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) .

## <a name="see-also"></a>Voir aussi
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Reprendre](../../../extensibility/debugger/reference/idebugthread2-resume.md)
