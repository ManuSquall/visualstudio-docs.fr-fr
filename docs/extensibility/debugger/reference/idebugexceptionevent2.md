---
title: IDebugExceptionEvent2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: dc6dacbac1092e211ba129417bd4e47aea31b733
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
Le moteur de débogage (DE) envoie cette interface pour le Gestionnaire de session de débogage (SDM) lorsqu’une exception est levée dans le programme en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugExceptionEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le D’implémente cette interface pour les rapports qu’une exception s’est produite dans le programme en cours de débogage. Le [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface doit être implémentée sur le même objet que cette interface. Le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à la `IDebugEvent2` interface.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Le crée et envoie cet objet d’événement pour signaler une exception. L’événement est envoyé à l’aide de la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fonction de rappel qui est fournie par le SDM lorsqu’il est attaché au programme en cours de débogage.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugExceptionEvent2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|Obtient des informations détaillées sur l’exception qui a déclenché cet événement.|  
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Obtient une description explicite de l’exception levée qui a déclenché cet événement.|  
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Détermine si le moteur de débogage (DE) prend en charge les transmettre cette exception au programme en cours de débogage lors de l’exécution se poursuit.|  
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Spécifie si l’exception doit être transmise au programme en cours de débogage lors de l’exécution se poursuit, ou si l’exception doit être ignorée.|  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Notes  
 Avant d’envoyer l’événement, le DE vérifie si cet événement d’exception a été désigné une exception de première chance ou de deuxième chance par un appel précédent à [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md). S’il a été désigné pour être une exception de première chance, les `IDebugExceptionEvent2` événement est envoyé à la SDM. Si ce n’est pas le cas, le DE donne une occasion de gérer l’exception à l’application. Si aucun gestionnaire d’exceptions n’est fourni, et si l’exception a été désignée comme une exception de deuxième chance, les `IDebugExceptionEvent2` événement est envoyé à la SDM. Dans le cas contraire, le DE reprend l’exécution du programme, et le système d’exploitation ou le runtime gère l’exception.  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)