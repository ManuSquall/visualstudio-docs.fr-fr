---
title: IDebugEntryPointEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEntryPointEvent2
helpviewer_keywords:
- IDebugEntryPointEvent2 interface
ms.assetid: a15d1cc3-97b7-438c-8d24-c23149708f42
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8def2d894da4a9a99b1e85cea9a595226e84c6f7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58950513"
---
# <a name="idebugentrypointevent2"></a>IDebugEntryPointEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Le moteur de débogage (dé) envoie cette interface pour le Gestionnaire de session de débogage (SDM) lorsque le programme est prêt à exécuter sa première instruction du code utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugEntryPointEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Le D’implémente cette interface dans le cadre de ses opérations normales. Le [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface doit être implémentée sur le même objet que cette interface. Utilise le SDM [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) pour accéder à la `IDebugEvent2` interface.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Le DE crée et envoie cet objet événement lorsque le programme en cours de débogage a été chargé et est prêt à exécuter la première instruction du code utilisateur. L’événement est envoyé à l’aide de la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fonction de rappel qui est fournie par le SDM lorsqu’il est attaché au programme en cours de débogage.  
  
## <a name="remarks"></a>Notes  
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) est envoyé lorsque le programme est prêt à exécuter la première instruction. Par exemple, `IDebugEntryPoint2` est envoyé lorsque le programme est prêt à exécuter l’utilisateur `main` (fonction).  
  
 Lorsque le D’envoie `IDebugEntryPointEvent2`, la position actuelle du code doit être à la première instruction du code utilisateur, comme `main`.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
