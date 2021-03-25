---
description: Reprend l’exécution d’un thread.
title: 'IDebugThread2 :: Resume | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 93552bac60d16a21212bfa89816481cf7099d399
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053020"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
Reprend l’exécution d’un thread.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Resume ( 
   DWORD *pdwSuspendCount
);
```

```csharp
int Resume ( 
   out uint pdwSuspendCount
);
```

## <a name="parameters"></a>Paramètres
`pdwSuspendCount`\
à Retourne le nombre de suspensions après l’opération de reprise.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Chaque appel à cette méthode décrémente le nombre de suspension jusqu’à ce qu’il atteigne la valeur 0, à laquelle l’exécution reprend en fait. Ce nombre de suspensions s’affiche dans la fenêtre de débogage des **Threads** .

 Pour chaque appel à cette méthode, il doit y avoir un appel antérieur à la méthode [suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) . Le nombre de suspensions détermine le nombre de fois `IDebugThread2::Suspend` que la méthode a été appelée jusqu’à présent.

## <a name="see-also"></a>Voir aussi
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Suspendre](../../../extensibility/debugger/reference/idebugthread2-suspend.md)
