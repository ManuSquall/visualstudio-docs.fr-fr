---
title: "&#39;Implements&#39; n’est pas valide pour les d&#233;clarations d’op&#233;rateur | Microsoft Docs"
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
  - "vbc33004"
  - "bc33004"
helpviewer_keywords: 
  - "BC33004"
ms.assetid: 22f27f4d-4bbd-4f8f-a6e8-0fc10efb268d
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Implements&#39; n’est pas valide pour les d&#233;clarations d’op&#233;rateur
Une [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement) spécifie le mot clé [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause).  
  
 Seule une procédure `Function` ou `Sub`, une propriété ou un événement peut implémenter un membre d’interface. Pour plus d’informations sur l’implémentation, consultez [NOT IN BUILD : Exemples d’implémentation d’interface en Visual Basic](http://msdn.microsoft.com/fr-fr/50bf2a30-73b6-4126-a921-075fd6eec278).  
  
 Une procédure `Operator` exige les deux mots clés `Public` et `Shared`, et un opérateur de conversion nécessite le mot clé `Widening` ou `Narrowing`. Pour plus d'informations, consultez [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures).  
  
 **ID d’erreur :** BC33004  
  
### Pour corriger cette erreur  
  
-   Si vous prévoyez que cette procédure implémente un membre d’interface, réécrivez\-la en tant que procédure `Function` ou `Sub`, propriété ou événement.  
  
-   Si cette procédure doit définir un opérateur, supprimez le mot clé `Implements` de sa déclaration.  
  
## Voir aussi  
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)