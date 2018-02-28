---
title: IDebugBreakEvent2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 3b58e0fb18b8f41f16a6cc92e682363ff531d5ec
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
Cette interface indique le Gestionnaire de session de débogage (SDM) qu’un saut de ligne asynchrone a été effectuée avec succès.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugBreakEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le D’implémente cette interface pour prendre en charge les sauts de l’utilisateur dans un programme. Le [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface doit être implémentée sur le même objet que cette interface (le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à la `IDebugEvent2` interface).  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Les appels SDM [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) lorsque l’utilisateur a demandé le programme en cours de débogage pour être suspendu. Lorsque le programme a correctement été suspendu, le D’envoie le `IDebugBreakEvent2` événement. Cet événement est envoyé à l’aide de la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fonction de rappel fournie par le SDM lorsqu’il est attaché au programme en cours de débogage.  
  
## <a name="remarks"></a>Notes  
 Par exemple, un utilisateur peut sélectionner la **interrompre tout** commande sur le **déboguer** menu pour sortir d’un programme qui exécute une boucle infinie. Le SDM indique au programme s’arrête en appelant [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md). L’envoie DE `IDebugBreakEvent2` lorsque le programme s’arrête finalement.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)