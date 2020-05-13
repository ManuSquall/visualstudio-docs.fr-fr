---
title: IDebugThread2::Resume Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3899dea7c33946588de4308f42b948ede703361a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718674"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
Reprend l’exécution d’un fil.

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
[out] Retourne le compte de suspension après l’opération de reprise.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Chaque appel à cette méthode décrément le compte de suspension jusqu’à ce qu’il atteigne 0 au moment où, l’exécution est effectivement repris. Ce compte de suspension est affiché dans la fenêtre **threads** débagé.

 Pour chaque appel à cette méthode, il doit y avoir un appel précédent à la méthode [Suspendre.](../../../extensibility/debugger/reference/idebugthread2-suspend.md) Le compte de suspension détermine `IDebugThread2::Suspend` combien de fois la méthode a été appelée jusqu’à présent.

## <a name="see-also"></a>Voir aussi
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Suspendre](../../../extensibility/debugger/reference/idebugthread2-suspend.md)
