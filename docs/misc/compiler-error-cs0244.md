---
title: "Erreur du compilateur CS0244 | Microsoft Docs"
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
  - "CS0244"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0244"
ms.assetid: f10e4479-ed6e-40dc-9fab-914e404d7f84
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0244
'is' et 'as' ne sont pas valides sur les types pointeur  
  
 Les mots clés [is](/dotnet/csharp/language-reference/keywords/is) et [as](/dotnet/csharp/language-reference/keywords/as) ne sont pas valides pour une utilisation sur les types de pointeurs. Pour plus d'informations, consultez [Pointeurs et code unsafe](/dotnet/csharp/programming-guide/unsafe-code-pointers/index).  
  
 L’exemple suivant génère l’erreur CS0244 :  
  
```  
// CS0244.cs // compile with: /unsafe class UnsafeTest { unsafe static void SquarePtrParam (int* p) { bool b = p is object;   // CS0244 p is pointer } unsafe public static void Main() { int i = 5; SquarePtrParam (&i); } }  
```