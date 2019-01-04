---
title: IDebugProgramCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramCreateEvent2
helpviewer_keywords:
- IDebugProgramCreateEvent2 interface
ms.assetid: b19a7934-6179-4a68-9075-bd7dcd640b05
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1213f37fbf4d7384155a17a5cf42c60b5d544f30
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53915031"
---
# <a name="idebugprogramcreateevent2"></a>IDebugProgramCreateEvent2
Cette interface est envoyée par le moteur de débogage (dé) pour le Gestionnaire de session de débogage (SDM) lorsqu’un programme est attaché à.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugProgramCreateEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 L’Allemagne ou le fournisseur de port personnalisé implémente cette interface pour signaler qu’un programme a été créé, généralement au moment où que le programme est attaché au. Le [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface doit être implémentée sur le même objet que cette interface. Le SDM utilise le `QueryInterface` méthode pour accéder à la `IDebugEvent2` interface.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 L’Allemagne ou le fournisseur de port personnalisé crée et envoie cet objet d’événement pour signaler la création d’un programme. Le D’envoie cet événement à l’aide de la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fonction de rappel qui est fournie par le SDM lorsqu’il est attaché au programme en cours de débogage. Le fournisseur de port personnalisé envoie cet événement à l’aide de la [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) interface.  
  
## <a name="remarks"></a>Notes  
 L’Allemagne ou le fournisseur de port personnalisé publie une nouvelle [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) interface en appelant [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)