---
title: "Fibre non planifi&#233;e | Microsoft Docs"
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
  - "bc30948"
  - "vbc30948"
helpviewer_keywords: 
  - "BC30948"
ms.assetid: 982bf6d2-ce62-4451-8a23-82dacf8ee100
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Fibre non planifi&#233;e
Le débogueur ne peut pas évaluer une expression, car elle est présente dans une fibre logique qui n’est pas planifiée sur un thread physique. Cela peut se produire si le processus est en cours d’exécution sur un serveur SQL à l’aide de fibres.  
  
 Une fibre se compose d’une pile et d’un contexte de registre, et elle peut s’exécuter sur n’importe quel thread. Elle peut être transférée hors d’un thread et redémarrée ultérieurement sur un autre thread.  
  
 **ID d’erreur :** BC30948  
  
### Pour corriger cette erreur  
  
-   Vérifiez que cette fibre est planifiée sur un thread physique.  
  
## Voir aussi  
 [Debugging SQL](http://msdn.microsoft.com/fr-fr/f27c17e6-1d90-49f2-9fc0-d02e6a27f109)   
 [Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md)