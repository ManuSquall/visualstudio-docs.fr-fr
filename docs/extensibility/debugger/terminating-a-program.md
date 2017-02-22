---
title: "Arr&#234;t d&#39;un programme | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "programmes, les événements d'arrêt"
  - "débogage (débogage SDK), afin d'arrêter un programme"
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Arr&#234;t d&#39;un programme
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Voici une description de l'arrêt d'un programme unique avec un thread.  
  
## processus d'arrêt  
  
1.  Le De envoie [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) avec [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)valide.  
  
2.  Le De envoie [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) avec [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)valide.  
  
 L'IDE passe en mode Design.  Les appels [IDebugPortNotify2 : : RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) du moteur de débogage ou l'environnement d'exécution pour supprimer le programme du port.  
  
## Voir aussi  
 [Appeler les événements de débogueur](../../extensibility/debugger/calling-debugger-events.md)