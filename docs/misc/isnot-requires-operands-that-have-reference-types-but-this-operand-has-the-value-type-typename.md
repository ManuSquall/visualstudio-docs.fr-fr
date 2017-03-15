---
title: "&#39;IsNot&#39; requiert des op&#233;randes qui ont des types r&#233;f&#233;rence, mais cet op&#233;rande a le type valeur &#39;&lt;nom_type&gt;&#39;. | Microsoft Docs"
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
  - "bc31419"
  - "vbc31419"
helpviewer_keywords: 
  - "BC31419"
ms.assetid: c44d2936-8c07-443a-b320-ac2bfbc1e9ec
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;IsNot&#39; requiert des op&#233;randes qui ont des types r&#233;f&#233;rence, mais cet op&#233;rande a le type valeur &#39;&lt;nom_type&gt;&#39;.
Une expression utilise [IsNot Operator](/dotnet/visual-basic/language-reference/operators/isnot-operator) avec au moins une opérande de type valeur.  
  
 L’opérateur `IsNot` détermine si deux références d’objet font référence à des objets différents. Il compare les valeurs de pointeur des types référence et n’a donc aucun sens avec des types de valeur.  
  
 **ID d’erreur :** BC31419  
  
### Pour corriger cette erreur  
  
-   Si vous souhaitez comparer les valeurs de deux types valeur, utilisez l’opérateur de comparaison `=` ou `<>`.  
  
-   Si vous souhaitez comparer les pointeurs de deux types référence, veillez à utiliser des références d’objet pour les deux opérandes. Vous pouvez utiliser des variables de référence ou des éléments, comme le mot clé [Me](http://msdn.microsoft.com/fr-fr/a65973c7-cf06-4547-9b25-9fba885525c2), qui se comportent comme des variables de référence.  
  
## Voir aussi  
 [Comparison Operators in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators)   
 [How to: Test Whether Two Objects Are the Same](../Topic/How%20to:%20Test%20Whether%20Two%20Objects%20Are%20the%20Same%20\(Visual%20Basic\).md)