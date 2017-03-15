---
title: "Erreur du compilateur CS0754 | Microsoft Docs"
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
  - "CS0754"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0754"
ms.assetid: c83e04b5-6ab5-45c2-805e-0ba4f041d506
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0754
Une méthode partielle ne peut pas implémenter explicitement une méthode d’interface.  
  
 Une méthode partielle ne peut pas être déclarée en tant qu’implémentation explicite d’une méthode définie dans une interface.  
  
### Pour corriger cette erreur  
  
1.  Supprimez la qualification d’interface explicite de la déclaration de méthode.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0754 :  
  
```  
// cs0754.cs using System; public interface IF { void Part(); } public partial class C : IF { partial void IF.Part(); //CS0754 public static int Main() { return 1; } }  
```  
  
## Voir aussi  
 [Implémentation d’interface explicite](/dotnet/csharp/programming-guide/interfaces/explicit-interface-implementation)   
 [Classes et méthodes partielles](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)