---
description: Obtient la raison pour laquelle le moteur DE débogage (DE) souhaite s’arrêter.
title: 'IDebugCanStopEvent2 :: GetReason | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2125bb90693d5a4c5cc23ac1225d56dea636de2e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085050"
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
