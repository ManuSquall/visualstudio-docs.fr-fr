---
title: IDebugBreakEvent2 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e1a2f9fede9119b4db0baf45e61213bcb2b5b67c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49177760"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface indique au Gestionnaire de débogage de session (SDM) qu’un saut de ligne asynchrone a été effectuée avec succès.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugBreakEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Le D’implémente cette interface pour prendre en charge les sauts de l’utilisateur dans un programme. Le [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface doit être implémentée sur le même objet que cette interface (utilise le SDM [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) pour accéder à la `IDebugEvent2` interface).  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Les appels SDM [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) lorsque l’utilisateur a demandé le programme en cours de débogage pour être suspendu. Lorsque le programme a correctement été suspendu, l’Allemagne envoie le `IDebugBreakEvent2` événement. Cet événement est envoyé à l’aide de la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fonction de rappel fournie par le SDM lorsqu’il est attaché au programme en cours de débogage.  
  
## <a name="remarks"></a>Notes  
 Par exemple, un utilisateur peut sélectionner la **interrompre tout** commande sur le **déboguer** menu quitter un programme qui exécute une boucle infinie. Le SDM indique au programme d’arrêter en appelant [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md). L’envoie DE `IDebugBreakEvent2` lorsque le programme s’arrête enfin.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)

