---
title: IDebugEventCallback2::Event | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 461c2487c18cb6edc5601868c0f9644d7b8eeac1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62874602"
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
Envoie une notification d’événements de débogage.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Event( 
   IDebugEngine2*  pEngine,
   IDebugProcess2* pProcess,
   IDebugProgram2* pProgram,
   IDebugThread2*  pThread,
   IDebugEvent2*   pEvent,
   REFIID          riidEvent,
   DWORD           dwAttrib
);
```

```csharp
int Event( 
   IDebugEngine2  pEngine,
   IDebugProcess2 pProcess,
   IDebugProgram2 pProgram,
   IDebugThread2  pThread,
   IDebugEvent2   pEvent,
   ref Guid       riidEvent,
   uint           dwAttrib
);
```

#### <a name="parameters"></a>Paramètres
 `pEngine`

 [in] Un [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) objet qui représente le moteur de débogage (dé) qui envoie cet événement. Un dé est requis pour remplir ce paramètre.

 `pProcess`

 [in] Un [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) objet qui représente le processus dans lequel l’événement se produit. Ce paramètre est renseigné par le Gestionnaire de session de débogage (SDM). Un dé transmet toujours une valeur null pour ce paramètre.

 `pProgram`

 [in] Un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objet qui représente le programme dans lequel cet événement se produit. Pour la plupart des événements, ce paramètre n’est pas une valeur null.

 `pThread`

 [in] Un [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objet qui représente le thread dans lequel cet événement se produit. Pour les événements d’arrêt, ce paramètre ne peut pas être une valeur null le frame de pile est obtenu à partir de ce paramètre.

 `pEvent`

 [in] Un [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) objet qui représente l’événement de débogage.

 `riidEvent`

 [in] GUID qui identifie quelle interface d’événement pour obtenir de le `pEvent` paramètre.

 `dwAttrib`

 [in] Une combinaison d’indicateurs de la [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) énumération.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Lors de l’appel de cette méthode, le `dwAttrib` paramètre doit correspondre à la valeur retournée par la [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) transmis à la méthode comme appelée sur l’objet d’événement dans le `pEvent` paramètre.

 Tous les événements de débogage sont validées de façon asynchrone, qu’un événement lui-même soit asynchrone ou non. Lorsqu’un D’appelle cette méthode, la valeur de retour n’indique pas si l’événement a été traitée, uniquement si l’événement a été reçu. En fait, dans la plupart des cas, l’événement n'a pas été traité lorsque cette méthode est retournée.

## <a name="see-also"></a>Voir aussi
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)