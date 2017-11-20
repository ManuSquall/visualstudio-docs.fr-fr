---
title: Processus | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f295dd93580caee4b6288febf7e83c09736b6080
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="processes"></a>Processus
En termes de l’architecture du débogueur, une **processus**:  
  
-   Est un conteneur pour un ensemble de programmes. Il est très similaire à un processus Windows, qui est un conteneur pour un ensemble de threads.  
  
-   Peut identifier par son nom, identificateur ou identificateur physique.  
  
-   Peut énumérer tous les programmes en cours d’exécution (et leurs threads).  
  
-   Peut décrire lui-même, le port qu’il est en cours d’exécution dans et l’ordinateur qui le contient.  
  
-   Peut créer un ou plusieurs programmes, de mettre fin à tous les programmes qu’il crée ou de provoquer un blocage du programme.  
  
-   Est représenté par un [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) interface, qui est créé lorsque le processus est appelé. Un processus est lancé par le Gestionnaire de débogage de session (SDM) ou [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
 Le package de débogage peut attacher un moteur de débogage (DE) à un processus en appelant [attacher](../../extensibility/debugger/reference/idebugprocess2-attach.md). Cela signifie que le DE joint à tous les programmes possibles en cours d’exécution dans le processus qu’il peut gérer. Par exemple, si le common language runtime DE attaché à un processus, il se connecte uniquement à des programmes qui sont en cours d’exécution du code managé.  
  
## <a name="see-also"></a>Voir aussi  
 [Programmes](../../extensibility/debugger/programs.md)   
 [Threads](../../extensibility/debugger/threads.md)   
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [Déboguer le Package](../../extensibility/debugger/debug-package.md)   
 [Moteur de débogage](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Attacher](../../extensibility/debugger/reference/idebugprocess2-attach.md)