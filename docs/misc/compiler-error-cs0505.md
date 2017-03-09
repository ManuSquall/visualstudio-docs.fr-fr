---
title: "Erreur du compilateur CS0505 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0505"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0505"
ms.assetid: e3cb9e33-7338-4869-859b-81d7439f0d23
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0505
'membre1' : substitution impossible, car 'membre2' n’est pas une fonction  
  
 Une déclaration de classe a tenté de substituer un élément qui n’est pas une méthode dans une classe de base. Les substitutions doivent correspondre au type de membre. Si la présence d’une méthode de même nom qu’une méthode contenue dans une classe de base est souhaitée, utilisez [new](/dotnet/csharp/language-reference/keywords/new) \(et non [override](/dotnet/csharp/language-reference/keywords/override)\) dans la déclaration de méthode de la classe de base.  
  
 L’exemple suivant génère l’erreur CS0505 :  
  
```  
// CS0505.cs // compile with: /target:library public class clx { public int i; } public class cly : clx { public override int i() { return 0; }   // CS0505 }  
```