---
title: "Avertissement du compilateur (niveau&#160;2) CS0469 | Microsoft Docs"
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
  - "CS0469"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0469"
ms.assetid: 773925ce-a8b2-4098-9ead-b96197442848
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;2) CS0469
La valeur 'goto case' n’est pas implicitement convertible en type 'type'  
  
 Quand vous utilisez `goto case`, une conversion implicite de la valeur du goto case vers le type du commutateur doit avoir lieu.  
  
## Exemple  
 L’exemple suivant génère l’avertissement CS0469.  
  
```  
// CS0469.cs // compile with: /W:2 class Test { static void Main() { char c = (char)180; switch (c) { case (char)127: break; case (char)180: goto case 127;   // CS0469 // try the following line instead // goto case (char) 127; } } }  
```