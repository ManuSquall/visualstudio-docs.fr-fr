---
title: 'IDebugCanStopEvent2 :: GetReason | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734526"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
Obtient la raison pour laquelle le moteur DE débogage (DE) souhaite s’arrêter.

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
à Retourne une valeur de l’énumération [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) qui décrit la raison de cet événement.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette méthode est généralement appelée avant la méthode [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) , de sorte que l’appelant peut déterminer s’il faut passer une valeur différente de zéro ( `TRUE` ) à la `IDebugCanStopEvent2::CanStop` méthode.

 La raison de l’arrêt peut être `CANSTOP_ENTRYPOINT` , ce qui signifie que le de a atteint un point d’entrée, ou `CANSTOP_STEPIN` , ce qui signifie que le de a effectué un pas à pas détaillé dans une fonction.

## <a name="see-also"></a>Voir aussi
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)
- [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)
