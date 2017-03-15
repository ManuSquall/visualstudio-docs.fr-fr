---
title: "Erreur du compilateur CS0762 | Microsoft Docs"
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
  - "CS0762"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0762"
ms.assetid: 7cedd1af-ffe6-4ca7-82fb-faa9e98014a4
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0762
Impossible de créer un délégué à partir de la méthode 'méthode', car il s’agit d’une méthode partielle sans déclaration d’implémentation  
  
 Une méthode partielle n’a pas besoin d’une déclaration d’implémentation. Cependant, la méthode encapsulée d’un délégué doit avoir une implémentation.  
  
### Pour corriger cette erreur  
  
1.  Fournissez une implémentation pour la méthode qui est utilisée pour initialiser le délégué.  
  
## Exemple  
  
```  
public delegate void TestDel(); public partial class C { partial void Part(); public static int Main() { C c = new C(); TestDel td = new TestDel(c.Part); // CS0762 return 1; } }  
```