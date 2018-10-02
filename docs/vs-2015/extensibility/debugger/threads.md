---
title: Threads | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8070107a1befab999f2edd47d32e25e84266b86d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501826"
---
# <a name="threads"></a>Threads
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Threads](https://docs.microsoft.com/visualstudio/extensibility/debugger/threads).  
  
En termes d’architecture du débogueur, une **thread**:  
  
-   Est l’unité fondamentale de calcul. Un thread exécute séquentiellement ses instructions dans le contexte d’une seule pile d’appels, déplacement à partir du contexte d’un code à l’autre.  
  
-   Peut identifier lui-même et le programme est en cours d’exécution et peut être nommé, suspendu et repris. Un thread peut également énumérer ses frames de pile associée et, sous certaines conditions, peut être déplacé vers un autre frame de pile. Étant donné le contexte d’un frame de pile, un thread peut retourner son thread logique associé, le cas échéant. Un thread a des propriétés, telles que d’un compteur de suspension, ce qui peut être affiché dans la fenêtre Threads de l’IDE.  
  
-   Est représenté par un [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) interface, généralement créé par un moteur de débogage (dé) ou d’une machine virtuelle en raison de l’exécution d’un programme.  
  
## <a name="see-also"></a>Voir aussi  
 [Programmes](../../extensibility/debugger/programs.md)   
 [Frames de pile](../../extensibility/debugger/stack-frames.md)   
 [Moteur de débogage](../../extensibility/debugger/debug-engine.md)   
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [Gestionnaire du débogage de session](../../extensibility/debugger/session-debug-manager.md)

