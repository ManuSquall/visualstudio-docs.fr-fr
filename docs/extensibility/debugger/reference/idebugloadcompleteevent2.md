---
title: IDebugLoadCompleteEvent2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugLoadCompleteEvent2
helpviewer_keywords: IDebugLoadCompleteEvent2
ms.assetid: 37eb7360-28e9-4273-862a-4c17f22af690
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b755e1f8fb8a4835b22a47fa245a27838c11089e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugloadcompleteevent2"></a>IDebugLoadCompleteEvent2
Cette interface est envoyée par le moteur de débogage (DE) pour le Gestionnaire de session de débogage (SDM) lorsque le programme est chargé, mais avant l’exécution de code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugLoadCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le D’implémente cette interface pour signaler que le programme a été chargé avec succès. Le [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface doit être implémentée sur le même objet que cette interface. Le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à la `IDebugEvent2` interface.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Le crée et envoie cet objet d’événement pour signaler que le programme a été chargé avec succès. L’événement est envoyé à l’aide de la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fonction de rappel qui est fournie par le SDM lorsqu’il est attaché au programme en cours de débogage.  
  
## <a name="remarks"></a>Remarques  
 Cet événement est un événement d’arrêt et qu’il doit avoir le `EVENT_STOPPING` l’indicateur est défini sur les attributs d’événement.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)