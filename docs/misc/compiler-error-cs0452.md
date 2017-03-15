---
title: "Erreur du compilateur CS0452 | Microsoft Docs"
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
  - "CS0452"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0452"
ms.assetid: 50a87734-fe07-4bce-891d-a76e131db6cc
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0452
Le type 'nom\_type' doit être un type de référence afin d’être utilisé comme paramètre 'nom\_paramètre' dans le type ou la méthode générique 'identificateur\_générique'  
  
 Cette erreur se produit quand vous passez un type de valeur tel que `struct` ou `int` en tant que paramètre à un type ou une méthode générique qui possède une contrainte de type référence.  
  
## Exemple  
 Le code suivant génère l’erreur CS0452.  
  
```  
// CS0452.cs using System; public class BaseClass<S> where S : class { } public class Derived1 : BaseClass<int> { } // CS0452 public class Derived2<S> : BaseClass<S> where S : struct { } // CS0452  
```  
  
## Voir aussi  
 [Contraintes sur les paramètres de type](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)