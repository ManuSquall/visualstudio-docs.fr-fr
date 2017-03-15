---
title: "Erreur du compilateur CS0133 | Microsoft Docs"
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
  - "CS0133"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0133"
ms.assetid: b5be456f-824d-4e6d-802b-0b1b5889efbd
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0133
L’expression assignée à 'variable' doit être constante  
  
 Une variable [const](/dotnet/csharp/language-reference/keywords/const) ne peut pas prendre comme valeur une expression qui n’est pas constante. Pour plus d'informations, consultez [Constantes](/dotnet/csharp/programming-guide/classes-and-structs/constants).  
  
 L’exemple suivant génère l’erreur CS0133 :  
  
```  
// CS0133.cs public class MyClass { public const int i = c;   // CS0133, c is not constant public static int c = i; // try the following line instead // public const int i = 6; public static void Main() { } }  
```