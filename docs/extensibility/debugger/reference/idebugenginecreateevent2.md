---
title: IDebugEngineCreateEvent2 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngineCreateEvent2
helpviewer_keywords:
- IDebugEngineCreateEvent2 interface
ms.assetid: 37c0a841-1c8d-4802-a990-36b54bca3ef7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c10522a869ff279c81e06aca53c3d06b453cdff6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31111847"
---
# <a name="idebugenginecreateevent2"></a>IDebugEngineCreateEvent2
Le moteur de débogage (DE) envoie cette interface pour le Gestionnaire de session de débogage (SDM) lors de la création d’une instance de la DE.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugEngineCreateEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le D’implémente cette interface dans le cadre de ses opérations normales. Le [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface doit être implémentée sur le même objet que cette interface (le SDM utilise le `QueryInterface` méthode pour accéder à la `IDebugEvent2` interface).  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Le DE crée et envoie cet objet d’événement lorsque la D’ont été instanciée. L’événement est envoyé à l’aide de la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fonction de rappel qui est fournie par le SDM lorsqu’il est attaché au programme en cours de débogage.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugEngineCreateEvent2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)|Récupère l’objet qui représente le moteur de débogage qui vient d’être créé (DE).|  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)