---
title: "La variable de contr&#244;le Next ne correspond pas &#224; la variable de contr&#244;le de boucle For &#39;&lt;nom_variable&gt;&#39;. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30070"
  - "bc30070"
helpviewer_keywords: 
  - "BC30070"
ms.assetid: e9e96008-b053-4fa0-8966-decaad99fecd
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La variable de contr&#244;le Next ne correspond pas &#224; la variable de contr&#244;le de boucle For &#39;&lt;nom_variable&gt;&#39;.
La variable de contrôle dans l’instruction `Next` d’une boucle `For...Next` doit correspondre à la variable dans l’instruction `For` correspondante.  
  
 **ID d’erreur :** BC30070  
  
### Pour corriger cette erreur  
  
1.  Vérifiez l’orthographe de la variable dans l’instruction `Next` et dans l’instruction `For` correspondante pour être certain qu’elle concorde.  
  
2.  Vérifiez qu’aucune partie de la boucle englobante n’a été supprimée par inadvertance.  
  
3.  Si cette boucle fait partie d’un ensemble de boucles imbriquées, vérifiez que chaque boucle se termine correctement.  
  
## Voir aussi  
 [For...Next, instruction](/dotnet/visual-basic/language-reference/statements/for-next-statement)