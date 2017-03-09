---
title: "Erreur du compilateur CS0623 | Microsoft Docs"
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
  - "CS0623"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0623"
ms.assetid: c9fd6888-b9c5-48bf-b25b-2fae1446ad24
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0623
Les initialiseurs de tableau ne peuvent être utilisés que dans un initialiseur de champ ou de variable. Essayez plutôt d’utiliser une expression new.  
  
 Une tentative a été effectuée pour initialiser un tableau à l’aide d’un initialiseur de tableau dans un contexte où il n’est pas autorisé.  
  
## Exemple  
 L’exemple suivant produit l’erreur CS0623, car le compilateur interprète \\{4\\} en tant qu’initialiseur de tableau incorporé à l’intérieur de l’initialiseur de tableau externe :  
  
```  
//cs0632.cs using System; class X { public int[] x = { 2, 3, {4}}; //CS0623 }  
```  
  
## Voir aussi  
 [Tableaux](/dotnet/csharp/programming-guide/arrays/index)