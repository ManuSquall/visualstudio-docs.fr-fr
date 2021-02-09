---
title: 'IDebugThread2 :: Resume | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6156becc782adb054af37cf24efd64915729149c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893722"
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

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Remarques
 Chaque appel à cette méthode décrémente le nombre de suspension jusqu’à ce qu’il atteigne la valeur 0, à laquelle l’exécution reprend en fait. Ce nombre de suspensions s’affiche dans la fenêtre de débogage des **Threads** .

 Pour chaque appel à cette méthode, il doit y avoir un appel antérieur à la méthode [suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) . Le nombre de suspensions détermine le nombre de fois `IDebugThread2::Suspend` que la méthode a été appelée jusqu’à présent.

## <a name="see-also"></a>Voir aussi
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Suspendre](../../../extensibility/debugger/reference/idebugthread2-suspend.md)
