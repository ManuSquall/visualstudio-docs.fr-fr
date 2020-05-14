---
title: IDebugEventCallback2::Event ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0b60c09b21d531326e343dddd2f1cc69cfb0e5d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729892"
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
Envoie une notification des événements de débogé.

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
[dans] Un objet [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) qui représente le moteur de débogé (DE) qui envoie cet événement. Un DE est nécessaire pour remplir ce paramètre.

`pProcess`\
[dans] Un objet [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) qui représente le processus dans lequel l’événement se produit. Ce paramètre est rempli par le gestionnaire de débogé de session (SDM). Un DE passe toujours une valeur nulle pour ce paramètre.

`pProgram`\
[dans] Un objet [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui représente le programme dans lequel cet événement se produit. Pour la plupart des événements, ce paramètre n’est pas une valeur nulle.

`pThread`\
[dans] Un objet [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) qui représente le fil dans lequel cet événement se produit. Pour l’arrêt des événements, ce paramètre ne peut pas être une valeur nulle que le cadre de pile est obtenu à partir de ce paramètre.

`pEvent`\
[dans] Un objet [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) qui représente l’événement de débogé.

`riidEvent`\
[dans] GUID qui identifie l’interface d’événement à obtenir à partir du `pEvent` paramètre.

`dwAttrib`\
[dans] Une combinaison de drapeaux de l’énumération [EVENTATTRIBUTES.](../../../extensibility/debugger/reference/eventattributes.md)

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Lors de l’appel de cette méthode, le `dwAttrib` paramètre doit correspondre à la valeur retournée de la méthode [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) comme appelé sur l’objet d’événement passé dans le `pEvent` paramètre.

 Tous les événements de débopathie sont affichés asynchronement, indépendamment du fait qu’un événement lui-même est asynchrone ou non. Lorsqu’un DE appelle cette méthode, la valeur de déclaration n’indique pas si l’événement a été traité, seulement si l’événement a été reçu. En fait, dans la plupart des cas, l’événement n’a pas été traité lorsque cette méthode revient.

## <a name="see-also"></a>Voir aussi
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
