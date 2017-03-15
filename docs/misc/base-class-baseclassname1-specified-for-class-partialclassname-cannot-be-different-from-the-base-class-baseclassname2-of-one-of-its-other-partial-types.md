---
title: "La classe de base &#39;&lt;nom_classe_de_base1&gt;&#39; sp&#233;cifi&#233;e pour la classe &#39;&lt;nom_classe_partielle&gt;&#39; ne peut pas &#234;tre diff&#233;rente de la classe de base &#39;&lt;nom_classe_de_base2&gt;&#39; de l’un de ses autres types partiels | Microsoft Docs"
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
  - "BC30928"
  - "vbc30928"
helpviewer_keywords: 
  - "BC30928"
ms.assetid: da464f09-1016-4dec-beb7-3202cacd8e1e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La classe de base &#39;&lt;nom_classe_de_base1&gt;&#39; sp&#233;cifi&#233;e pour la classe &#39;&lt;nom_classe_partielle&gt;&#39; ne peut pas &#234;tre diff&#233;rente de la classe de base &#39;&lt;nom_classe_de_base2&gt;&#39; de l’un de ses autres types partiels
Une classe est définie dans deux déclarations partielles ou plus, qui contiennent plusieurs [Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement) spécifiant plusieurs classes de base.  
  
 Quand vous divisez la définition d’une classe en plusieurs déclarations partielles, le compilateur traite la classe comme l’union de toutes ses déclarations partielles. Cela s’applique non seulement aux membres, mais également à l’implémentation, à l’héritage et au niveau d’accès.  
  
 Une classe peut implémenter plusieurs interfaces, mais elle ne peut pas hériter de plusieurs classes de base. Ainsi, toutes les instructions `Inherits` doivent spécifier la même classe de base.  
  
 **ID d’erreur :** BC30928  
  
### Pour corriger cette erreur  
  
-   Déterminez quelle classe doit être la classe de base de votre classe partielle, et supprimez de ses déclarations partielles toute instruction `Inherits` qui spécifie une autre classe de base.  
  
## Voir aussi  
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)