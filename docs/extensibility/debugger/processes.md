---
title: "Processus | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "débogage (débogage SDK), traite"
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Processus
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Quant à l'architecture du débogueur, **un processus**:  
  
-   est un conteneur pour un ensemble de programmes.  Il est fortement similaire à un processus windows, qui est un conteneur pour un ensemble de thread.  
  
-   Peut s'identifient de nom, l'identificateur, ou l'identificateur physique.  
  
-   Peut énumérer tous les programmes en cours de exécution \(et leurs thread\).  
  
-   Peut se décrire, le port qu'il s'exécute, et l'ordinateur qui le contient.  
  
-   Peut créer un ou plusieurs programmes, arrêter des programmes l'un des qu'il crée, ou provoque l'arrêt un programme.  
  
-   Est représenté par une interface d' [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) , qui est créée lorsque le processus est lancé.  Lancement d'un processus par soit le gestionnaire ou [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)\(SDM\) de débogage de session.  
  
 Le package de débogage peut attacher un moteur de débogage \(DE\) à un processus en appelant [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md).  Cela signifie que le De s'attache à tous les programmes possibles en cours de exécution dans le processus qu'il peut exécuter.  Par exemple, si le common langage runtime De s'attache à un processus, il est attaché uniquement aux programmes qui exécutent le code managé.  
  
## Voir aussi  
 [Programs](../../extensibility/debugger/programs.md)   
 [Threads](../../extensibility/debugger/threads.md)   
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [Déboguer le Package](../../extensibility/debugger/debug-package.md)   
 [Moteur de débogage](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)