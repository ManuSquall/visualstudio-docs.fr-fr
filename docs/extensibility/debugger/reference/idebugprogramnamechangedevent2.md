---
title: IDebugProgramNameChangedEvent2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugProgramNameChangedEvent2 interface
ms.assetid: be1f1cd5-0b2f-435c-a052-dca28a7c978d
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 90bc1312835797e6863d9b931e13d03ccea1f985
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogramnamechangedevent2"></a>IDebugProgramNameChangedEvent2
Envoyé à partir du moteur de débogage (DE) pour le Gestionnaire de session de débogage (SDM) lorsque le nom d’un programme change.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugProgramNameChangedEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le D’implémente cette interface au rapport que le nom du programme a changé. Le [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface doit être implémentée sur le même objet que cette interface. Le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à la **IDebugEvent2** interface.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Le crée et envoie cet objet d’événement pour signaler un changement de nom de programme. Le D’envoie cet événement à l’aide de la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fonction de rappel qui est fournie par le SDM lorsqu’il est attaché au programme en cours de débogage. Le fournisseur de port personnalisé envoie cet événement à l’aide de l’interface le.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll