---
title: "Erreur du compilateur CS0462 | Microsoft Docs"
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
  - "CS0462"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0462"
ms.assetid: 0732b12d-0f7a-47d5-bc54-8b6147d7249f
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0462
Les membres hérités 'member1' et 'member2' ont la même signature dans le type 'type' et ne peuvent donc pas être substitués  
  
 Cette erreur se produit avec l’introduction de génériques. Normalement, vous ne pouvez pas avoir deux versions d’une méthode dans une classe avec la même signature. Mais avec les génériques, vous pouvez spécifier une méthode générique qui peut dupliquer une autre méthode si elle est instanciée avec un type particulier.  
  
## Exemple  
 Quand `C<int>` est instancié, deux versions de la méthode `F` sont créées avec la même signature, donc le remplacement dans la classe `D` ne peut pas déterminer celle à laquelle appliquer le remplacement.  
  
 L’exemple suivant génère l’erreur CS0462.  
  
```  
// CS0462.cs // compile with: /target:library class C<T> { public virtual void F(T t) {} public virtual void F(int t) {} } class D : C<int> { public override void F(int t) {}   // CS0462 }  
```