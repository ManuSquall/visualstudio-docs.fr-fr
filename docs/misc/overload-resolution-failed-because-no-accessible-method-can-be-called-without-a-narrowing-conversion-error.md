---
title: "La r&#233;solution de surcharge a &#233;chou&#233;, car aucun &#39;&lt;m&#233;thode&gt;&#39; accessible ne peut &#234;tre appel&#233; sans conversion restrictive&#160;: &lt;erreur&gt; | Microsoft Docs"
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
  - "vbc30519"
  - "bc30519"
helpviewer_keywords: 
  - "BC30519"
ms.assetid: 3b3e724d-6fad-4146-b47d-6525493b2fa8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La r&#233;solution de surcharge a &#233;chou&#233;, car aucun &#39;&lt;m&#233;thode&gt;&#39; accessible ne peut &#234;tre appel&#233; sans conversion restrictive&#160;: &lt;erreur&gt;
Vous avez effectué un appel vers une méthode surchargée, mais le compilateur ne peut pas trouver les méthodes qui peuvent être appelées sans conversion restrictive. Une conversion restrictive modifie une valeur en un type de données qui peut ne pas pouvoir contenir certaines valeurs possibles.  
  
 **ID d’erreur :** BC30519  
  
### Pour corriger cette erreur  
  
-   Spécifiez `Option Strict Off`.  
  
## Voir aussi  
 [Overloaded Properties and Methods](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)