---
title: "Interruption de requ&#234;te en attente | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30947"
  - "bc30947"
helpviewer_keywords: 
  - "BC30947"
ms.assetid: 6bc4df1b-e833-47c7-9568-9ced67a2af5d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Interruption de requ&#234;te en attente
Dans le débogueur Visual Studio, une expression spécifie un appel de procédure, mais il existe une requête d’interruption du thread.  
  
 Le débogueur n’essaie pas d’appeler une procédure sur un thread qui n’est pas actif.  
  
 **ID d’erreur :** BC30947  
  
### Pour corriger cette erreur  
  
-   Si possible, déterminez la source de la requête d’interruption du thread, pour pouvoir l’empêcher de se reproduire.  
  
-   Arrêtez et redémarrez le débogage.  
  
## Voir aussi  
 [Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [How to: Start Execution](http://msdn.microsoft.com/fr-fr/b0fe0ce5-900e-421f-a4c6-aa44ddae453c)   
 [How to: Stop Debugging or Stop Execution](http://msdn.microsoft.com/fr-fr/03c68f95-aa96-481b-990e-467e065453a5)   
 [Code Stepping Overview](http://msdn.microsoft.com/fr-fr/8791dac9-64d1-4bb9-b59e-8d59af1833f9)   
 [Expressions dans Visual Basic](../Topic/Expressions%20in%20Visual%20Basic.md)