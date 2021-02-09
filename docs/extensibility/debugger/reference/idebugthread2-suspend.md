---
title: 'IDebugThread2 :: suspend | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ede08dfd2c5f8ee3a205f744388d9aac3f8f3709
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893657"
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

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Remarques
 Chaque appel à cette méthode incrémente le nombre de suspensions au-dessus de 0. Ce nombre de suspensions s’affiche dans la fenêtre de débogage des **Threads** .

 Pour chaque appel à cette méthode, il doit y avoir un appel ultérieur à la méthode [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) .

## <a name="see-also"></a>Voir aussi
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Reprendre](../../../extensibility/debugger/reference/idebugthread2-resume.md)
