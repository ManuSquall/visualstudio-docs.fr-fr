---
title: IDebugEvent2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 0d783cb13ee227e317afe9b49abedb6f53e9fa76
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugevent2"></a>IDebugEvent2
Cette interface est utilisée pour communiquer des informations de débogage critiques, tels que l’arrêt à un point d’arrêt et les informations non critiques, par exemple un message de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le moteur de débogage (DE) et le fournisseur de port personnalisé implémentent cette interface sur le même objet en tant que toutes les autres interfaces d’événements.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 À l’aide de l’argument ID (IID) donné à interface [événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ou [événement](../../../extensibility/debugger/reference/idebugportevents2-event.md), le Gestionnaire de session de débogage (SDM) appelle [QueryInterface](/cpp/atl/queryinterface) sur la `IDebugEvent2` interface à obtenir l’interface d’événements approprié.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugEvent2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Obtient les attributs de cet événement de débogage.|  
  
## <a name="remarks"></a>Notes  
 Interfaces de l’événement plus spécifique, tel que [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), ne dérivent pas de l’interface IDebugEvent2, mais sont plutôt implémentées comme une interface distincte sur le même objet en tant que `IDebugEvent2`.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Événement](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)