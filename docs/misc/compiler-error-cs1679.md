---
title: "Erreur du compilateur CS1679 | Microsoft Docs"
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
  - "CS1679"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1679"
ms.assetid: c42e9bca-212a-458e-88f8-b81c812436bb
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1679
Alias extern non valide pour '\/reference' ; 'identifier' n’est pas un identificateur valide  
  
 Quand vous utilisez la fonctionnalité d’alias d’assembly externe de l’option **\/reference**, le texte qui suit **\/reference:** et qui précède le signe \= doit être un identificateur ou un mot clé C\# valide selon la spécification du langage C\#.  
  
 Pour corriger cette erreur, remplacez le texte avant le signe \= par un identificateur ou un mot clé C\# valide.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1679.  
  
```  
// CS1679.cs // compile with: /reference:123$BadIdentifier%=System.dll class TestClass { static void Main() { } }  
```