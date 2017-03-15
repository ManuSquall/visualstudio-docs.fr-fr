---
title: "Erreur du compilateur CS0211 | Microsoft Docs"
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
  - "CS0211"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0211"
ms.assetid: 720be9a9-b0c1-4391-94e5-4c4027e83036
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0211
Impossible de prendre l'adresse de l'expression donnée  
  
 Vous pouvez prendre l’adresse des champs, des variables locales et des indirections de pointeurs, mais vous ne pouvez pas prendre, par exemple, l’adresse de la somme de deux variables locales. Pour plus d'informations, consultez [Pointeurs et code unsafe](/dotnet/csharp/programming-guide/unsafe-code-pointers/index).  
  
 L’exemple suivant génère l’erreur CS0211 :  
  
```  
// CS0211.cs // compile with: /unsafe public class MyClass { unsafe public void M() { int a = 0, b = 0; int *i = &(a + b);   // CS0211, the addition of two local variables // try the following line instead // int *i = &a; } public static void Main() { } }  
```