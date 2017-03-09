---
title: "Erreur du compilateur CS0314 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0314"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0314"
ms.assetid: 12f68f51-0568-4e80-b0fd-15899807477d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0314
Impossible d’utiliser le type 'type1' comme paramètre de type 'nom' dans le type ou la méthode générique 'nom'. Il n’y a pas de conversion boxing ou de conversion de paramètre de type de 'type1' en 'type2'.  
  
 Lorsqu’un type générique utilise un paramètre de type qui est contraint, la nouvelle classe doit aussi satisfaire à ces mêmes contraintes.  
  
### Pour corriger cette erreur  
  
1.  Dans l’exemple qui suit, ajoutez `where T : ClassConstraint` à la classe `B`.  
  
## Exemple  
 Le code suivant génère l’erreur CS0314 :  
  
```  
// cs0314.cs // Compile with: /target:library public class ClassConstraint { } public class A<T> where T : ClassConstraint { } public class B<T> : A<T> //CS0314 { } // Try using this instead. public class C<T> : A<T> where T : ClassConstraint { }  
```  
  
## Voir aussi  
 [Contraintes sur les paramètres de type](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)