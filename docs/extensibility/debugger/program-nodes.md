---
title: "Nœuds de programme | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "nœuds du programme, le contexte de débogage"
  - "débogage (débogage SDK), programme de nœuds"
  - "nœuds de programme, ajout"
  - "nœuds de programme, de remplacement"
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Nœuds de programme
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Quant à l'architecture du débogueur, **un nœud de programme**:  
  
-   est une description légère d'un programme.  
  
-   Peut s'identifier et le processus qu'il s'exécute, et peut être attaché, être détaché de, et décrire le moteur de débogage \(DE\) qui l'a créé, si nécessaire.  
  
-   Est représenté par une interface d' [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) , généralement créée par un De ou un port.  Des nœuds de programme sont ajoutés à un port en appelant [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md).  Lorsqu'un nœud de programme est ajouté à un port, il est ajouté au processus contenant le programme que ce nœud de programme représente.  
  
 Une journée ou l'autre fin de la session de débogage soit démarrée, selon l'implémentation du package de débogage, les nœuds de programme sont utilisés pour créer correspondre des programmes.  Lorsqu'un processus est interrogé sur ses programmes, des programmes sont énumérés, un pour chaque nœud de programme.  
  
 Avant qu'un programme soit attaché, l'IDE ne requiert qu'une description légère du programme.  Ces informations peuvent être obtenues à partir de le nœud de programme.  Une fois le programme est attaché, les besoins de l'IDE d'afficher davantage d'informations détaillées, telles qu'une liste de tous les threads qui s'exécutent dans le programme.  Ces informations sont obtenues à partir de le programme lui\-même.  
  
## Voir aussi  
 [Programs](../../extensibility/debugger/programs.md)   
 [Processus](../../extensibility/debugger/processes.md)   
 [Moteur de débogage](../../extensibility/debugger/debug-engine.md)   
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)