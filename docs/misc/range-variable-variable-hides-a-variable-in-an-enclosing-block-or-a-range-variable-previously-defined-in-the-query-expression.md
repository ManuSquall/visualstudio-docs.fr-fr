---
title: "La variable de port&#233;e &lt;variable&gt; masque une variable dans un bloc englobant ou une variable de port&#233;e pr&#233;c&#233;demment d&#233;finie dans l’expression de requ&#234;te | Microsoft Docs"
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
  - "bc30978"
  - "vbc30978"
helpviewer_keywords: 
  - "BC30978"
ms.assetid: 806d94c1-653f-40c0-b1c4-95661c76a392
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La variable de port&#233;e &lt;variable&gt; masque une variable dans un bloc englobant ou une variable de port&#233;e pr&#233;c&#233;demment d&#233;finie dans l’expression de requ&#234;te
Une variable de portée d’une requête porte le même nom qu’une variable définie précédemment dans la même portée, ou qu’une variable de portée précédemment définie dans la requête.  
  
 **ID d’erreur :** BC30978  
  
### Pour corriger cette erreur  
  
-   Vérifiez que les variables de portée de la requête ne portent pas le même nom que des variables existant dans la même portée.  
  
-   Mettez entre parenthèses les requêtes imbriquées portant le nom de variables de contrôle existantes, en séparant la portée de chaque variable de portée.  
  
## Voir aussi  
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)