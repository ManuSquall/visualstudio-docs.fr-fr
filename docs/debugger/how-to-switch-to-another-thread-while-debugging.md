---
title: "Comment&#160;: basculer vers un autre thread pendant un d&#233;bogage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "threads, commuter (débogage)"
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
caps.latest.revision: 26
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 26
---
# Comment&#160;: basculer vers un autre thread pendant un d&#233;bogage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lorsque vous déboguez une application multithread, plusieurs méthodes s'offrent à vous pour remplacer le contexte du thread avec lequel vous travaillez par un autre thread.  
  
### Pour basculer vers un thread figurant dans la fenêtre Threads  
  
-   Double\-cliquez sur le thread.  
  
### Pour basculer vers un thread dans une fenêtre source  
  
-   Dans la reliure gauche, cliquez avec le bouton droit sur un indicateur de thread, pointez sur **Basculer vers**, puis cliquez sur le nom du thread vers lequel vous voulez basculer.  Le menu contextuel contient uniquement les threads de cet emplacement spécifique.  
  
     Si aucun indicateur n'apparaît, cliquez avec le bouton droit dans la fenêtre **Threads** et vérifiez que l'option **Afficher les threads dans la source** est sélectionnée.  
  
### Pour basculer vers un thread dans la barre d'outils Emplacement de débogage  
  
1.  Dans la barre d'outils **Emplacement de débogage**, cliquez sur la zone **Thread**.  
  
2.  Dans la liste, cliquez sur le thread vers lequel vous souhaitez basculer.  
  
## Voir aussi  
 [Déboguer les applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)