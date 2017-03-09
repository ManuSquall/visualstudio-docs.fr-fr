---
title: "Erreur du compilateur CS0701 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0701"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0701"
ms.assetid: eb844e31-00bd-468d-9f77-11d10a4ef120
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0701
'identifier' n’est pas une contrainte valide. Un type utilisé comme contrainte doit être une interface, une classe non\-sealed ou un paramètre de type.  
  
 Cette erreur se produit si un type sealed est utilisé comme contrainte. Pour résoudre cette erreur, utilisez uniquement des types non\-sealed comme contraintes.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0701.  
  
```  
// CS0701.cs // compile with: /target:library class C<T> where T : System.String {}   // CS0701 class D<T> where T : System.Attribute {}   // OK  
```