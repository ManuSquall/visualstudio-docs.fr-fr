---
description: Envoie une notification d’événements de débogage.
title: 'IDebugEventCallback2 :: Event | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: afa0cfd8f96d21a510370a4fc526a3cae053c77b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152921"
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

## <a name="parameters"></a>Paramètres
`pEngine`\
dans Objet [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) qui représente le moteur de débogage (de) qui envoie cet événement. Un DE est requis pour remplir ce paramètre.

`pProcess`\
dans Objet [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) qui représente le processus dans lequel l’événement se produit. Ce paramètre est rempli par le gestionnaire de débogage de session (SDM). Un DE passe toujours une valeur null pour ce paramètre.

`pProgram`\
dans Objet [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui représente le programme dans lequel cet événement se produit. Pour la plupart des événements, ce paramètre n’est pas une valeur null.

`pThread`\
dans Objet [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) qui représente le thread dans lequel cet événement se produit. Pour les événements d’arrêt, ce paramètre ne peut pas être une valeur null, car le frame de pile est obtenu à partir de ce paramètre.

`pEvent`\
dans Objet [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) qui représente l’événement de débogage.

`riidEvent`\
dans GUID qui identifie l’interface d’événement à obtenir à partir du `pEvent` paramètre.

`dwAttrib`\
dans Combinaison d’indicateurs de l’énumération [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Lors de l’appel de cette méthode, le `dwAttrib` paramètre doit correspondre à la valeur retournée par la méthode [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) telle qu’elle est appelée sur l’objet d’événement passé dans le `pEvent` paramètre.

 Tous les événements de débogage sont publiés de manière asynchrone, qu’un événement lui-même soit asynchrone ou non. Quand un DE appelle cette méthode, la valeur DE retour n’indique pas si l’événement a été traité, uniquement si l’événement a été reçu. En fait, dans la plupart des cas, l’événement n’a pas été traité lorsque cette méthode est retournée.

## <a name="see-also"></a>Voir aussi
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
