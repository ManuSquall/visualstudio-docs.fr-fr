---
title: "Le param&#232;tre lambda &#39;&lt;param&#232;tre&gt;&#39; masque une variable dans un bloc englobant, une variable de port&#233;e pr&#233;c&#233;demment d&#233;finie ou une variable d&#233;clar&#233;e implicitement dans une expression de requ&#234;te. | Microsoft Docs"
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
  - "bc36641"
  - "vbc36641"
helpviewer_keywords: 
  - "BC36641"
ms.assetid: ee08c366-29d1-4abb-b14c-23ae2b9680e7
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le param&#232;tre lambda &#39;&lt;param&#232;tre&gt;&#39; masque une variable dans un bloc englobant, une variable de port&#233;e pr&#233;c&#233;demment d&#233;finie ou une variable d&#233;clar&#233;e implicitement dans une expression de requ&#234;te.
Une variable dans une expression lambda a le même nom qu’une variable précédemment définie dans la même portée. Il peut s’agir d’une variable dans un bloc de code englobant pour une expression lambda imbriquée, une variable de portée précédemment définie dans une requête LINQ ou une variable qui est déclarée implicitement pour une requête LINQ.  
  
 **ID d’erreur :** BC36641  
  
### Pour corriger cette erreur  
  
-   Vérifiez que toutes les variables dans l’expression lambda ont des noms uniques qui ne dupliquent pas des noms de variables existants dans la même portée.  
  
## Voir aussi  
 [Lambda Expressions](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)   
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)