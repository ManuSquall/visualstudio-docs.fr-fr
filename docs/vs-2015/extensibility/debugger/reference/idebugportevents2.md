---
title: IDebugPortEvents2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5e0f6455e6df8db88b1aae1a7b7f6965c0ee524b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68188526"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface indique à un écouteur (en général, le débogage Gestionnaire de session [SDM] ou un moteur de débogage) de la création de processus et un programme et de destruction sur un port particulier. Ces informations peuvent être utilisées pour présenter une vue en temps réel des processus et des programmes en cours d’exécution sur le port.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugPortEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 En général, Visual Studio implémente cette interface pour recevoir des notifications sur la création du programme et la destruction. Un moteur de débogage peut également implémenter cette interface pour écouter ces événements de port.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Tous les [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaces peuvent être interrogées pour une <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interface. Le <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> méthode pour `IDebugPortEvents2` est appelée le <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interface permettant d’obtenir un <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interface. Enfin, le <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> méthode dans le <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interface est appelée pour envoyer des événements via le [événement](../../../extensibility/debugger/reference/idebugportevents2-event.md) (méthode).  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente la méthode de `IDebugPortEvents2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Envoie les événements qui décrivent la création et la destruction des processus et des programmes sur le port.|  
  
## <a name="remarks"></a>Notes  
 `IDebugPortEvents2` est également utilisé par le SDM pour déboguer des programmes qui s’exécutent dans un processus déjà en cours de débogage.  
  
 Événements de port sont passés au SDM par cette interface.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
