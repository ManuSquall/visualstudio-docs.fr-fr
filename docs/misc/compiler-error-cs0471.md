---
title: "Erreur du compilateur CS0471 | Microsoft Docs"
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
  - "CS0471"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0471"
ms.assetid: 3b666461-c57b-45f4-83d3-a23786e29ae9
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0471
La méthode 'name' n’est pas une méthode générique. Si vous voulez une liste d’expressions, utilisez les parenthèses autour de l’expression \<.  
  
 Cette erreur se produit quand votre code contient une liste d’expressions sans parenthèses.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0471 :  
  
```  
// CS0471.cs // compile with: /t:library class Test { public void F(bool x, bool y) {} public void F1() { int a = 1, b = 2, c = 3; F(a<b, c>(3));    // CS0471 // To resolve, try the following instead: // F((a<b), c>(3)); } }  
  
```