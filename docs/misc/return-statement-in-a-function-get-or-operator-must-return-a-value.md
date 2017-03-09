---
title: "L’instruction &#39;Return&#39; dans un Function, Get ou Operator doit retourner une valeur | Microsoft Docs"
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
  - "bc30654"
  - "vbc30654"
helpviewer_keywords: 
  - "BC30654"
ms.assetid: af0fb1fc-1b2e-4cae-9768-10965cda5506
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’instruction &#39;Return&#39; dans un Function, Get ou Operator doit retourner une valeur
Les instructions `Return` doivent être utilisées pour retourner une valeur à une procédure appelante. Vous ne pouvez pas utiliser d’instructions `Return` seules pour contrôler le flux du programme.  
  
 **ID d’erreur :** BC30654  
  
### Pour corriger cette erreur  
  
1.  Spécifiez une valeur que la fonction ou la procédure peut retourner.  
  
2.  Utilisez l’instruction `End` pour faire en sorte que le programme quitte la procédure en cours.  
  
## Voir aussi  
 [Return Statement](/dotnet/visual-basic/language-reference/statements/return-statement)   
 [End \<keyword\> Statement](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)