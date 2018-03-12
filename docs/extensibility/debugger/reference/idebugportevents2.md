---
title: IDebugPortEvents2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 0a5782f0a50ac37b45c4b7e3402bcdded96b4683
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
Cette interface notifie un écouteur (en général, le débogage Gestionnaire de session [SDM] ou un moteur de débogage) de la création de processus et de programme et de destruction sur un port particulier. Ces informations peuvent être utilisées pour présenter une vue en temps réel des processus et des programmes en cours d’exécution sur le port.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugPortEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 En général, Visual Studio implémente cette interface pour recevoir des notifications sur la création d’un programme et de destruction. Un moteur de débogage peut également implémenter cette interface pour écouter ces événements de port.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Tous les [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaces peuvent être interrogées pour une <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interface. Le <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> méthode pour `IDebugPortEvents2` est appelée dans le <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interface à obtenir un <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interface. Enfin, le <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> méthode dans le <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interface est appelée pour envoyer les événements par le biais du [événement](../../../extensibility/debugger/reference/idebugportevents2-event.md) (méthode).  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente la méthode de `IDebugPortEvents2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Envoie les événements qui décrivent la création et la destruction des processus et des programmes sur le port.|  
  
## <a name="remarks"></a>Notes  
 `IDebugPortEvents2`est également utilisé par le SDM pour déboguer des programmes qui s’exécutent dans un processus déjà en cours de débogage.  
  
 Événements de port sont passés à la SDM par cette interface.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)