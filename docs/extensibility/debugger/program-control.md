---
title: "Contr&#244;le du programme | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "débogage [Debugging SDK], contrôle d'exécution"
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Contr&#244;le du programme
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dans le débogage Visual Studio, toutes les routines de progression et continues suivantes se produisent au niveau de programme :  
  
-   Définissant l'instruction suivante, c. autrement dit., en définissant votre ordinateur à l'instruction suivante à exécuter dans un environnement particulier de frame  
  
-   Exécuter, c. autrement dit., suite à quitter hors de le mode de progression  
  
-   progression à l'instruction suivante  
  
-   Reprendre le mode actuel de progression  
  
-   L'abandon les threads contenus par le programme  
  
-   La reprise des threads contenus par le programme  
  
> [!NOTE]
>  En affichant la pile des appels est implémentée au niveau de le thread.  Pour énumérer les informations de frame en consultant la pile des appels pour un thread, vous devez implémenter toutes les méthodes d'interface d' [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) .  
  
## Méthodes de contrôle du programme  
 Le tableau suivant répertorie les méthodes d' [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) qui doivent être implémentées pour un contrôle de façon moins fonctionnel \(DE\) de moteur de débogage et de l'exécution.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDebugProgram2 : : exécutez](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Continue à exécuter tous les threads contenus par un programme d'un état arrêté.  requis pour le contrôle d'exécution.|  
|[IDebugProgram2 : : continuez](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Continue à exécuter tous les threads contenus par un programme d'un état arrêté.  requis pour le contrôle d'exécution.|  
|[IDebugProgram2 : : étape](../../extensibility/debugger/reference/idebugprogram2-step.md)|Effectue une étape sur le thread donné.  Continue à exécuter tous les autres threads contenus par le programme.  requis pour le contrôle d'exécution.|  
  
 Pour les programmes multithread, vous devez également implémenter la méthode d' [IDebugProgram2 : : EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) et toutes les méthodes d'interface d' [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) .  
  
## Voir aussi  
 [Contrôle de l'exécution et l'évaluation de l'état](../../extensibility/debugger/execution-control-and-state-evaluation.md)