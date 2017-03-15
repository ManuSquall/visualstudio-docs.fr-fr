---
title: "Erreur du compilateur CS0449 | Microsoft Docs"
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
  - "CS0449"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0449"
ms.assetid: 32c07a2c-4c48-4d07-b643-72422a6b9fac
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0449
La contrainte 'class' ou 'struct' doit être placée avant toutes les autres contraintes  
  
 Les contraintes sur le paramètre de type d’un type ou d’une méthode générique doivent se produire dans un ordre spécifique : en premier `class` ou `struct`, le cas échéant, puis toutes les contraintes d’interface et enfin, toutes les contraintes de constructeur. Cette erreur est provoquée par la contrainte `class` ou `struct` qui n’apparaît pas en premier. Pour résoudre cette erreur, réorganisez les clauses de contrainte.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0449.  
  
```  
// CS0449.cs // compile with: /target:library interface I {} public class C4 { public void F1<T>() where T : class, struct, I {}   // CS0449 public void F2<T>() where T : I, struct {}   // CS0449 public void F3<T>() where T : I, class {}   // CS0449 // OK public void F4<T>() where T : class {} public void F5<T>() where T : struct {} public void F6<T>() where T : I {} }  
```