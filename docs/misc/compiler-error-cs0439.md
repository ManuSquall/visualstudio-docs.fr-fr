---
title: "Erreur du compilateur CS0439 | Microsoft Docs"
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
  - "CS0430"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0439"
ms.assetid: 5cbac869-1b1b-45f9-98c8-38c17348035f
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0439
Une déclaration d'alias extern doit précéder tous les autres éléments définis dans l'espace de noms  
  
 Cette erreur se produit quand une déclaration `extern` figure après un autre élément \(par exemple une déclaration `using`\) dans le même espace de noms. Les déclarations `extern` doivent précéder tous les autres éléments d’espace de noms.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0439 :  
  
```  
// CS0439.cs using System; extern alias MyType;   // CS0439 // To resolve the error, make the extern alias the first line in the file. public class Test { public static void Main() { } }  
```