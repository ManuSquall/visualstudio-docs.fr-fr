---
title: IDebugCanStopEvent2::GetReason | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f253fc622beb6eee3490b77a1531b0b2096f14a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56719039"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
Obtient la raison pour laquelle le moteur de débogage (dé) veut arrêter de raison.

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

#### <a name="parameters"></a>Paramètres
 `pcr`

 [out] Retourne une valeur de la [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) énumération qui décrit la raison de cet événement.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode est généralement appelée avant la [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) méthode afin que l’appelant puisse déterminer s’il faut passer zéro (`TRUE`) pour le `IDebugCanStopEvent2::CanStop` (méthode).

 La raison de l’arrêt peut être `CANSTOP_ENTRYPOINT`, ce qui signifie que l’Allemagne a atteint un point d’entrée, ou `CANSTOP_STEPIN`, ce qui signifie que l’Allemagne a exécuté le code dans une fonction.

## <a name="see-also"></a>Voir aussi
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)
- [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)