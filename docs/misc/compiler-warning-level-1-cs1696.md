---
title: "Avertissement du compilateur (niveau&#160;1) CS1696 | Microsoft Docs"
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
  - "CS1696"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1696"
ms.assetid: 69a45988-1aba-4a01-a84e-7ca59f8dde28
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;1) CS1696
Commentaire sur une seule ligne ou fin de ligne attendue  
  
 Le compilateur requiert qu’une directive de préprocesseur soit suivie d’une marque de fin de ligne ou d’un commentaire sur une seule ligne. Le compilateur a terminé le traitement d’une directive de préprocesseur valide et a rencontré un élément qui viole cette contrainte de syntaxe.  
  
## Exemple  
 L’exemple suivant génère l’avertissement CS1696.  
  
```  
// CS1696.cs class Test { public static void Main() { #pragma warning disable 1030;219   // CS1696 #pragma warning disable 1030   // OK } }  
```