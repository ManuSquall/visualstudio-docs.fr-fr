---
title: "La classe &#39;&lt;nom_classe&gt;&#39; n’a pas de &#39;Sub&#160;New&#39; accessible et ne peut pas &#234;tre h&#233;rit&#233;e. | Microsoft Docs"
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
  - "vbc31399"
  - "BC31399"
helpviewer_keywords: 
  - "BC31399"
ms.assetid: 035b333f-ff6a-4fc4-bd36-82f40b1d8bab
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La classe &#39;&lt;nom_classe&gt;&#39; n’a pas de &#39;Sub&#160;New&#39; accessible et ne peut pas &#234;tre h&#233;rit&#233;e.
Une classe utilise une instruction Inherits \([Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement)\) pour spécifier une classe de base, mais elle ne peut accéder à aucun constructeur sur la classe de base prévue.  
  
 Cela peut se produire si la classe de base prévue n’a pas de constructeurs ou si elle a des constructeurs dont les niveaux d’accès empêchent l’accès à partir d’une autre classe.  
  
 Lorsque vous héritez d’une classe, votre constructeur doit appeler le constructeur de classe de base à l’aide de [MyBase \- delete](http://msdn.microsoft.com/fr-fr/52491d06-6451-4f6f-9aa6-8fab59bbc2b9). Si vous n’effectuez pas cet appel, ou si vous n’écrivez pas un constructeur explicite, Visual Basic génère un constructeur implicite qui appelle `MyBase.New()`.  
  
 **ID d’erreur :** BC31399  
  
### Pour corriger cette erreur  
  
1.  Si vous disposez d’un contrôle de code source sur la classe de base prévue, modifiez le niveau d’accès d’au moins l’un de ses constructeurs afin qu’une autre classe puisse y accéder.  
  
2.  Si vous ne pouvez pas modifier les niveaux d’accès des constructeurs de la classe de base prévue, héritez d’une autre classe ou n’héritez pas du tout.  
  
## Voir aussi  
 [Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [MyBase \- delete](http://msdn.microsoft.com/fr-fr/52491d06-6451-4f6f-9aa6-8fab59bbc2b9)   
 [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [Access Levels in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)