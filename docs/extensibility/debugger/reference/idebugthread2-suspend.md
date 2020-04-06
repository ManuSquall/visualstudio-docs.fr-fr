---
title: IDebugThread2::Suspend Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 74a7dd5dc69effbd46986eff963de3e740d9aa8e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718641"
---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
Suspend un fil.

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
[out] Retourne le compte de suspension après l’opération de suspension.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Chaque appel à cette méthode incrémente le compte de suspension au-dessus de 0. Ce compte de suspension est affiché dans la fenêtre **threads** débagé.

 Pour chaque appel à cette méthode, il doit y avoir un appel ultérieur à la méthode [Resume.](../../../extensibility/debugger/reference/idebugthread2-resume.md)

## <a name="see-also"></a>Voir aussi
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Reprendre](../../../extensibility/debugger/reference/idebugthread2-resume.md)
