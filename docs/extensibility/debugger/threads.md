---
title: Threads | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0e53ca354bdf29dd004126a7de79b5d2648753f9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53889775"
---
# <a name="threads"></a>Threads
Dans l’architecture du débogueur, une *thread*:  
  
-   Est l’unité fondamentale de calcul. Un thread exécute séquentiellement ses instructions dans le contexte d’une seule pile d’appels, déplacement à partir du contexte d’un code à l’autre.  
  
-   Peut identifier lui-même et le programme, dans qu'il est en cours d’exécution. Threads peuvent être nommés, suspendus et repris. Un thread peut également énumérer ses frames de pile associée et, sous certaines conditions, peut être déplacé vers un autre frame de pile. Étant donné le contexte d’un frame de pile, un thread peut retourner son thread logique associé, le cas échéant. Un thread a des propriétés, telles que d’un compteur de suspension, qui peut être affiché dans le **Threads** fenêtre de l’IDE.  
  
-   Est représenté par un [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) interface, généralement créé par un moteur de débogage (dé) ou d’une machine virtuelle en raison de l’exécution d’un programme.  
  
## <a name="see-also"></a>Voir aussi  
 [Programmes](../../extensibility/debugger/programs.md)   
 [Frames de pile](../../extensibility/debugger/stack-frames.md)   
 [Moteur de débogage](../../extensibility/debugger/debug-engine.md)   
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [Gestionnaire de session de débogage](../../extensibility/debugger/session-debug-manager.md)