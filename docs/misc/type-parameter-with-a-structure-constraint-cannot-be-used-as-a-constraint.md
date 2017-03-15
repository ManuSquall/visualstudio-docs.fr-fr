---
title: "Un param&#232;tre de type avec une contrainte &#39;Structure&#39; ne peut pas &#234;tre utilis&#233; en tant que contrainte | Microsoft Docs"
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
  - "vbc32114"
  - "bc32114"
helpviewer_keywords: 
  - "BC32114"
ms.assetid: 442b2048-9dc4-4223-bcfc-4d96bf8d14de
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Un param&#232;tre de type avec une contrainte &#39;Structure&#39; ne peut pas &#234;tre utilis&#233; en tant que contrainte
Un paramètre de type avec une contrainte `Structure` est utilisé en tant que contrainte pour un autre paramètre de type.  
  
 La contrainte `Structure` impose que l’argument de type passé à son paramètre de type soit un type valeur. Toutefois, un type valeur ne peut pas être implémenté ou hérité. Son utilisation en tant que contrainte n’est donc pas significative, car il faudrait que l’autre paramètre de type l’implémente ou en hérite.  
  
 La seule interprétation significative de cette situation est que les deux arguments de type doivent être exactement du même type. Si tel est le cas, votre type générique a besoin d’un seul paramètre de type.  
  
 L’instruction suivante peut générer cette erreur.  
  
 `Class c1(Of t1 As Structure, t2 As t1)`  
  
 Le type passé à `t2` ne peut pas implémenter ou hériter du type passé à `t1`, car le type passé à `t1` doit être un type valeur.  
  
 **ID d’erreur :** BC32114  
  
### Pour corriger cette erreur  
  
-   Supprimez le paramètre de type contraint à `Structure` de la liste des contraintes sur l’autre paramètre de type.  
  
-   Si les deux paramètres de type nécessitent le même type de valeur, définissez le type générique avec un seul paramètre de type.  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Structure \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)