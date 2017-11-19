---
title: IDebugEntryPointEvent2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEntryPointEvent2
helpviewer_keywords: IDebugEntryPointEvent2 interface
ms.assetid: a15d1cc3-97b7-438c-8d24-c23149708f42
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e8f6a5052943da57bc73beacdec8fc94a2b27164
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugentrypointevent2"></a>IDebugEntryPointEvent2
Le moteur de débogage (DE) envoie cette interface pour le Gestionnaire de session de débogage (SDM) lorsque le programme est prêt à exécuter sa première instruction du code utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugEntryPointEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le D’implémente cette interface dans le cadre de ses opérations normales. Le [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface doit être implémentée sur le même objet que cette interface. Le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à la `IDebugEvent2` interface.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Le DE crée et envoie cet objet d’événement lorsque le programme en cours de débogage a été chargé et est prêt à exécuter la première instruction du code utilisateur. L’événement est envoyé à l’aide de la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fonction de rappel qui est fournie par le SDM lorsqu’il est attaché au programme en cours de débogage.  
  
## <a name="remarks"></a>Remarques  
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) est envoyé lorsque le programme est prêt à exécuter la première instruction. Par exemple, `IDebugEntryPoint2` est envoyé lorsque le programme est prêt à exécuter l’utilisateur `main` (fonction).  
  
 Lorsque le D’envoie `IDebugEntryPointEvent2`, la position actuelle du code doit être à la première instruction du code utilisateur, comme `main`.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)