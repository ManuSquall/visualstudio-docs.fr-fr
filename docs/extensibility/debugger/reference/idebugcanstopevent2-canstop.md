---
description: Indique au moteur de débogage s’il faut ou non arrêter à l’emplacement de code actuel ou simplement continuer l’exécution.
title: 'IDebugCanStopEvent2 :: CanStop | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 38b4d528ae1aa5a89853dc4873a9c07aa051a14c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102173634"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
Indique au moteur de débogage s’il faut ou non arrêter à l’emplacement de code actuel ou simplement continuer l’exécution.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CanStop ( 
   BOOL fCanStop
);
```

```csharp
int CanStop ( 
   int fCanStop
);
```

## <a name="parameters"></a>Paramètres
`fCanStop`\
dans Différent de zéro ( `TRUE` ) si le de doit s’arrêter à l’emplacement de code actuel ; sinon, zéro ( `FALSE` ).

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Le récepteur de cet événement appelle généralement la méthode [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) pour déterminer la raison pour laquelle le de souhaite s’arrêter, puis appelle la `IDebugCanStopEvent2::CanStop` méthode avec la réponse appropriée.

 Si le DE s’arrête, il envoie un événement qui décrit la raison de l’arrêt. Il y a généralement deux événements qui sont envoyés, un saut d’utilisateur ou de signal représenté par l’interface [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) et un événement de point d’arrêt représenté par l’interface [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) .

## <a name="see-also"></a>Voir aussi
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
