---
title: "Les arguments ne peuvent pas &#234;tre pass&#233;s &#224; un &#39;New&#39; utilis&#233; pour un param&#232;tre de type | Microsoft Docs"
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
  - "BC32085"
  - "vbc32085"
helpviewer_keywords: 
  - "BC32085"
ms.assetid: a60bf62d-2b2e-4621-b8db-e67720b918fb
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les arguments ne peuvent pas &#234;tre pass&#233;s &#224; un &#39;New&#39; utilis&#233; pour un param&#232;tre de type
Une déclaration ou une instruction d’assignation appelle un type générique et fournit des arguments de constructeur à un paramètre de type qui possède la contrainte [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator).  
  
 Une liste de contraintes appliquée à un paramètre de type peut spécifier que l’argument de type passé à ce paramètre de type doit exposer un constructeur sans paramètre et accessible par le code de création. Un paramètre de type ne peut pas demander un constructeur qui accepte les paramètres, et un paramètre de type avec la contrainte `New` ne peut pas accepter ce constructeur.  
  
 **ID d’erreur :** BC32085  
  
### Pour corriger cette erreur  
  
-   Supprimez la liste d’arguments située après l’argument de type dans l’instruction qui appelle le type générique. Vous ne pouvez pas passer d’arguments de constructeur au paramètre de type correspondant.  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)