---
title: "Modes de fonctionnement | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "moteurs de débogage, modes"
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Modes de fonctionnement
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Il existe trois modes dans lesquels l'IDE peut s'exécuter, comme suit :  
  
-   [Mode design](#vsconoperationalmodesanchor1)  
  
-   [mode exécution](#vsconoperationalmodesanchor2)  
  
-   [Mode arrêt](#vsconoperationalmodesanchor3)  
  
 Comment les transitions personnalisées \(DE\) du moteur de débogage entre les modes est une décision d'implémentation nécessitant que vous soyez familiarisé avec les mécanismes de transition.  Le De peut ou directement ne pas implémenter ces modes.  Ces modes sont en réalité des modes de package de débogage qui ont basculé sur l'action utilisateur ou les événements du De.  Par exemple, le passage du mode exécution en mode arrêt est incitée par un événement arrêtant du De.  Le passage du saut en mode exécution ou en mode pas \- à \- pas est incitée par l'utilisateur effectuant des opérations telles que l'étape ou exécute.  Pour plus d'informations sur LE passage, consultez [Contrôle de l'exécution](../../extensibility/debugger/control-of-execution.md).  
  
##  <a name="vsconoperationalmodesanchor1"></a> Mode design  
 Le mode Design est l'état non exécuté de débogage de Visual Studio, pendant ce temps vous pouvez définir des fonctionnalités de débogage dans votre application.  
  
 Uniquement certaines fonctionnalités de débogage sont utilisées en mode Design.  Un développeur peut choisir de définir des points d'arrêt ou de créer des expressions de l'illustre.  Le De n'est jamais chargé ou est appelé pendant que l'IDE est en mode Design.  L'interaction avec le De se produit pendant l'exécution et les modes arrêt seulement.  
  
##  <a name="vsconoperationalmodesanchor2"></a> mode exécution  
 Mode exécution se produit lorsqu'un programme s'exécute dans une session de débogage dans l'IDE.  L'application s'exécute jusqu'à l'arrêt, jusqu'à ce qu'un point d'arrêt soit atteint, ou jusqu'à ce qu'une exception est levée.  Lorsque l'application s'exécute à l'arrêt, DE transitions en mode Design.  Lorsqu'un point d'arrêt est atteint ou une exception est levée, DE transitions en mode arrêt.  
  
##  <a name="vsconoperationalmodesanchor3"></a> Mode arrêt  
 Mode Arrêt se produit lorsque l'exécution du programme de débogage est interrompue.  Mode Arrêt permet au développeur un instantané de l'application au moment de le saut et permet au développeur pour analyser l'état de l'application et la modification la manière dont l'application s'exécutera.  Le développeur peut afficher et de modifier du code, examiner ou modifier des données, redémarrer l'application, arrêter l'exécution, ou continuer l'exécution de la même point.  
  
 Mode Arrêt est écrit lorsque le De envoie un événement arrêtant synchrone.  Les événements cessants synchrones, également appelés événements cessants, informent le gestionnaire de débogage de session \(SDM\) et l'IDE que l'application est déboguée a cessé d'exécuter le code.  Les interfaces d' [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) et d' [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) sont des exemples d'événements d'arrêt.  
  
 Arrêt des événements sont repris par un appel à l'une des méthodes suivantes, qui transition le débogueur du mode arrêt d'exécution ou en mode pas \- à \- pas :  
  
-   [Exécuter](../../extensibility/debugger/reference/idebugprocess3-execute.md)  
  
-   [Étape](../../extensibility/debugger/reference/idebugprocess3-step.md)  
  
-   [Continuer](../../extensibility/debugger/reference/idebugprocess3-continue.md)  
  
###  <a name="vsconoperationalmodesanchor4"></a> Mode pas \- à \- pas  
 Le mode pas \- à \- pas se produit lorsque les étapes de programme à la ligne de code suivante, ou dans, sur, ou à partir d'une fonction.  Une étape est effectuée en appelant la méthode [Étape](../../extensibility/debugger/reference/idebugprocess3-step.md).  Cette méthode requiert `DWORD`s qui spécifient les énumérations de [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) et de [STEPKIND](../../extensibility/debugger/reference/stepkind.md) comme paramètres d'entrée.  
  
 Lorsque le programme effectue un pas correctement une ligne de code suivante ou dans une fonction, ou elle s'exécute au curseur ou à un point d'arrêt défini, de les transitions automatiquement à nouveau en mode arrêt.  
  
## Voir aussi  
 [Contrôle de l'exécution](../../extensibility/debugger/control-of-execution.md)