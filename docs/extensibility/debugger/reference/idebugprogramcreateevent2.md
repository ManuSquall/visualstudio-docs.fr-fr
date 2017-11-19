---
title: IDebugProgramCreateEvent2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramCreateEvent2
helpviewer_keywords: IDebugProgramCreateEvent2 interface
ms.assetid: b19a7934-6179-4a68-9075-bd7dcd640b05
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2e61b838c922d0b25a7b0bef71c3cf1f15ec8843
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogramcreateevent2"></a>IDebugProgramCreateEvent2
Cette interface est envoyée par le moteur de débogage (DE) pour le Gestionnaire de session de débogage (SDM) lorsqu’un programme est attaché à.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugProgramCreateEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le DE ou le fournisseur de port personnalisé implémente cette interface pour signaler qu’un programme a été créé, généralement au moment où que le programme est attaché au. Le [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface doit être implémentée sur le même objet que cette interface. Le SDM utilise le `QueryInterface` méthode pour accéder à la `IDebugEvent2` interface.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Le DE ou le fournisseur de port personnalisé crée et envoie cet objet d’événement pour signaler la création d’un programme. Le D’envoie cet événement à l’aide de la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fonction de rappel qui est fournie par le SDM lorsqu’il est attaché au programme en cours de débogage. Le fournisseur de port personnalisé envoie cet événement à l’aide de la [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) interface.  
  
## <a name="remarks"></a>Remarques  
 Le DE ou le fournisseur de port personnalisé publie une nouvelle [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) interface en appelant [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)