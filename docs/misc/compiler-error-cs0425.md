---
title: "Erreur du compilateur CS0425 | Microsoft Docs"
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
  - "CS0425"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0425"
ms.assetid: cec0391c-a641-43bc-8557-92b23f6ca685
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0425
Les contraintes pour le paramètre de type 'paramètre de type' de la méthode 'méthode' doivent correspondre aux contraintes pour le paramètre de type 'paramètre de type' de la méthode d’interface 'méthode'. Utilisez plutôt une implémentation d’interface explicite.  
  
 Cette erreur se produit quand une méthode générique virtuelle est substituée dans une classe dérivée et que les contraintes de la méthode de la classe dérivée ne correspondent pas aux contraintes de la méthode de la classe de base. Pour éviter cette erreur, assurez\-vous que la clause `where` est identique dans les deux déclarations, ou implémentez l’interface explicitement.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0425 :  
  
```  
// CS0425.cs class C1 { } class C2 { } interface IBase { void F<ItemType>(ItemType item) where ItemType : C1; } class Derived : IBase { public void F<ItemType>(ItemType item) where ItemType : C2  // CS0425 { } } class CMain { public static void Main() { } }  
```  
  
## Exemple  
 La correspondance des contraintes ne doit pas forcément être exacte. Il suffit que l’ensemble de contraintes possède la même signification. Par exemple, le code suivant est acceptable :  
  
```  
// CS0425b.cs interface J<Z> { } interface I<S> { void F<T>(S s, T t) where T: J<S>, J<int>; } class C : I<int> { public void F<X>(int s, X x) where X : J<int> { } public static void Main() { } }  
```