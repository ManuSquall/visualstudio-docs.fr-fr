---
title: "Impossible d’h&#233;riter de l’interface &#39;&lt;nom_interface1&gt;&#39;, car elle peut &#234;tre identique &#224; l’interface &#39;&lt;nom_interface2&gt;&#39; dont l’interface &#39;&lt;nom_interface3&gt;&#39; h&#233;rite pour certains arguments de type | Microsoft Docs"
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
  - "bc32123"
  - "vbc32123"
helpviewer_keywords: 
  - "BC32123"
ms.assetid: 2b8fa1f0-3d43-45c6-99d0-328151479b43
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible d’h&#233;riter de l’interface &#39;&lt;nom_interface1&gt;&#39;, car elle peut &#234;tre identique &#224; l’interface &#39;&lt;nom_interface2&gt;&#39; dont l’interface &#39;&lt;nom_interface3&gt;&#39; h&#233;rite pour certains arguments de type
Une interface générique hérite d’au moins deux interfaces génériques, et deux des héritages peuvent entrer en conflit pour certaines valeurs d’arguments de type.  
  
 Les instructions suivantes peuvent générer cette erreur.  
  
```  
Public Interface interfaceA(Of u) End Interface Public Interface interfaceX(Of v) Inherits interfaceA(Of v) End Interface Public Interface derivedInterface(Of t1, t2) Inherits interfaceA(Of t1), interfaceX(Of t2) End Interface  
```  
  
 Si `derivedInterface` est construit ou implémenté en fournissant le même type à `t1` et à `t2`, il doit hériter de deux versions de `interfaceA` avec des arguments de type identiques. Il en résulte une ambiguïté quant à la version à laquelle accéder.  
  
 **ID d’erreur :** BC32123  
  
### Pour corriger cette erreur  
  
-   Modifiez l’un des arguments de type fournis à l’interface dérivée pour éviter tout conflit.  
  
     ou  
  
-   Supprimez de l’instruction `Inherits` l’une des interfaces provoquant le conflit potentiel d’héritage ou d’implémentation.  
  
## Voir aussi  
 [NOT IN BUILD : Vue d’ensemble des interfaces](http://msdn.microsoft.com/fr-fr/f96bb470-c1b8-4c73-89bc-6f536b798da1)   
 [Interface Statement](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)