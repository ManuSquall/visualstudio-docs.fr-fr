---
title: "Erreur du compilateur CS0406 | Microsoft Docs"
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
  - "CS0406"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0406"
ms.assetid: 9d69681c-e261-4e5e-9361-ea566de12f2e
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0406
La contrainte de type classe 'constraint' doit être placée avant toute autre contrainte  
  
 Quand un type ou une méthode générique possède une contrainte de type classe, cette contrainte doit figurer en premier. Pour éviter cette erreur, déplacez la contrainte de type classe au début de la liste des contraintes.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0406 :  
  
```  
// CS0406.cs // compile with: /target:library interface I {} class C {} class D<T> where T : I, C {}   // CS0406 class D2<T> where T : C, I {}   // OK  
```