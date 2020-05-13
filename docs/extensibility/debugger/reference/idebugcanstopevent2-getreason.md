---
title: IDebugCanStopEvent2::GetReason - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59e611c3ed69528f92a6085cf74aa44efed09144
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734526"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
Obtient la raison pour laquelle le moteur de débogé (DE) veut s’arrêter.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetReason( 
   CANSTOP_REASON* pcr
);
```

```csharp
int GetReason( 
   out enum_CANSTOP_REASON pcr
);
```

## <a name="parameters"></a>Paramètres
`pcr`\
[out] Retourne une valeur de [l’énumération CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) qui décrit la raison de cet événement.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette méthode est généralement appelée avant la méthode [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) afin que l’appelant peut déterminer s’il faut passer non-zéro (`TRUE`) à la `IDebugCanStopEvent2::CanStop` méthode.

 La raison de l’arrêt peut être soit `CANSTOP_ENTRYPOINT`, ce `CANSTOP_STEPIN`qui signifie que le DE a atteint un point d’entrée, ou , ce qui signifie que le DE est entré dans une fonction.

## <a name="see-also"></a>Voir aussi
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)
- [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)
