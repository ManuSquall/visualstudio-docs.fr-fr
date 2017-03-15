---
title: "Erreur du compilateur CS1578 | Microsoft Docs"
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
  - "CS1578"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1578"
ms.assetid: 8356cd33-5acc-4db7-8bbd-2d25f9d7728e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1578
Nom de fichier, commentaire sur une seule ligne ou fin de ligne attendu  
  
 Après une directive [\#line](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-line), seul un nom de fichier \(entre guillemets doubles\) ou un commentaire sur une ligne est autorisé.  
  
 L’exemple suivant génère l’erreur CS1578 :  
  
```  
// CS1578.cs class MyClass { static void Main() { #line 101 abc.cs   // CS1578 // try the following line instead //#line 101 "abc.cs" intt i;          // error will be reported on line 101 } }  
```