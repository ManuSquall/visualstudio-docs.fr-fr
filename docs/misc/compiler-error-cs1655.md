---
title: "Erreur du compilateur CS1655 | Microsoft Docs"
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
  - "CS1655"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1655"
ms.assetid: 041e9daa-c026-494f-b086-0db9a23c969b
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1655
Impossible de passer les champs de 'variable' en tant qu’argument ref ou out, car il s’agit d’un 'readonly variable type'  
  
 Cette erreur se produit si vous tentez de passer un membre d’une variable [foreach](/dotnet/csharp/language-reference/keywords/foreach-in), d’une variable [using](/dotnet/csharp/language-reference/keywords/using-statement) ou d’une variable [fixed](/dotnet/csharp/language-reference/keywords/fixed-statement) à une fonction en tant qu’argument ref ou out. Étant donné que ces variables sont considérées en lecture seule dans ces contextes, cela n’est pas autorisé.  
  
 L’exemple suivant génère l’erreur CS1655 :  
  
```  
// CS1655.cs struct S { public int i; } class CMain { static void f(ref int iref) { } public static void Main() { S[] sa = new S[10]; foreach(S s in sa) { CMain.f(ref s.i);  // CS1655 } } }  
```