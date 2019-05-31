---
title: IDebugOutputStringEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugOutputStringEvent2
helpviewer_keywords:
- IDebugOutputStringEvent2 interface
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d47fe2b329f9f2fb4adb57cdf6e2a6a871299d14
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311897"
---
# <a name="idebugoutputstringevent2"></a>IDebugOutputStringEvent2
Cette interface est envoyée par le moteur de débogage (dé) pour le Gestionnaire de session de débogage (SDM) à une chaîne de sortie.

## <a name="syntax"></a>Syntaxe

```
IDebugOutputStringEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Le D’implémente cette interface pour envoyer une chaîne à la **sortie** fenêtre de l’IDE. Le [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface doit être implémentée sur le même objet que cette interface. Utilise le SDM [QueryInterface](/cpp/atl/queryinterface) pour accéder à la `IDebugEvent2` interface.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Le DE crée et envoie cet objet d’événement pour envoyer une chaîne à la **sortie** fenêtre. L’événement est envoyé à l’aide de la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fonction de rappel qui est fournie par le SDM lorsqu’il est attaché au programme en cours de débogage.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente la méthode de `IDebugOutputStringEvent2`.

|Méthode|Description|
|------------|-----------------|
|[GetString](../../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)|Obtient le message peut être affichée.|

## <a name="remarks"></a>Notes
 Par exemple, dans le code non managé, la chaîne de sortie peut provenir lorsque le programme débogué envoie une chaîne vers Win32 `OutputDebugString` (fonction). Cette chaîne est interceptée par l’Allemagne et envoyée au SDM comme le `IDebugOutputStringEvent2` événement.

 Utilisez [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) pour envoyer un message qui requiert une réponse de l’utilisateur.

 Utilisez [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) pour envoyer un message d’erreur qui ne nécessite pas de réponse.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)