---
title: "Concepts du d&#233;bogueur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "débogage (débogage SDK)"
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Concepts du d&#233;bogueur
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

À partir de le package de débogage de Visual Studio, vous devez être familiarisé avec les concepts architecturaux utilisés en concevant le package.  
  
## Dans cette section  
 [La Session de débogage](../../extensibility/debugger/debug-session.md)  
 Explique le rôle d'une session dans l'architecture de débogage.  
  
 [Serveurs](../../extensibility/debugger/servers-visual-studio-sdk.md)  
 Explique ce qu'est un serveur en termes de architecture de débogage, dans les deux termes abstraits et physiques.  
  
 [Fournisseurs de port](../../extensibility/debugger/port-suppliers.md)  
 Explique ce qu'est un fournisseur de port par rapport à l'architecture de débogage.  
  
 [Ports](../../extensibility/debugger/ports.md)  
 Explique ce qu'est un port par rapport à l'architecture de débogage.  
  
 [Processus](../../extensibility/debugger/processes.md)  
 Explique ce qu'est un processus en termes de architecture de débogage.  
  
 [Nœuds de programme](../../extensibility/debugger/program-nodes.md)  
 Définit un nœud de programme par rapport à l'architecture de débogage, inclure comment elle peut s'identifier et processus qu'il est exécuté.  
  
 [Programs](../../extensibility/debugger/programs.md)  
 Définit un programme par rapport à l'architecture de débogage.  
  
 [Threads](../../extensibility/debugger/threads.md)  
 Définit les caractéristiques des threads en termes de architecture de débogage.  
  
 [Frames de pile](../../extensibility/debugger/stack-frames.md)  
 Définit un frame de pile par rapport à l'architecture de débogage.  un frame de pile est une abstraction d'une pile qui fournit le contexte d'exécution d'un thread.  
  
 [Modules](../../extensibility/debugger/modules.md)  
 Définit un module, quant à l'architecture de débogage, comme conteneur physique de code, tel qu'un fichier exécutable ou une DLL.  
  
 [Points d’arrêt](../../extensibility/debugger/breakpoints-visual-studio-sdk.md)  
 Définit les trois types de point d'arrêt\-en attente, de la limite, et erreur\-dans des termes d'architecture de débogage.  
  
## Rubriques connexes  
 [Contextes de débogueur](../../extensibility/debugger/debugger-contexts.md)  
 Explique comment le moteur de \(DE\) débogage s'exécute simultanément dans le code, la documentation, et des contextes d'évaluation de l'expression.  Décrit, pour les trois contextes, de l'emplacement, de la position, ou l'évaluation pertinentes à celui\-ci.  
  
 [Composants du débogueur](../../extensibility/debugger/debugger-components.md)  
 Fournit une vue d'ensemble des composants de débogage de Visual Studio, notamment le moteur de \(DE\) débogage, l'évaluateur \(EE\) d'expression, et le gestionnaire de symboles \(SH\).  
  
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)  
 Contient des liens vers différentes tâches de débogage, telles que exécuter un programme et évaluer des expressions.