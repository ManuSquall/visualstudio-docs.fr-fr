---
title: "Erreur du compilateur CS0077 | Microsoft Docs"
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
  - "CS0077"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0077"
ms.assetid: 55d3d290-d172-41a3-b326-ebf5a0a7e81f
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0077
L’opérateur as doit être utilisé avec un type référence ou un type Nullable \('int' est un type valeur qui n’autorise pas les valeurs null\).  
  
 Un [type valeur](/dotnet/csharp/language-reference/keywords/value-types) a été passé à l’opérateur [as](/dotnet/csharp/language-reference/keywords/as). Comme `as` peut retourner [null](/dotnet/csharp/language-reference/keywords/null), seuls des [types référence](/dotnet/csharp/language-reference/keywords/reference-types) ou un type Nullable peuvent lui être passés. Pour plus d’informations sur les types Nullable, consultez [Types Nullable](/dotnet/csharp/programming-guide/nullable-types/index).  
  
 L’exemple suivant génère l’erreur CS0077 :  
  
```  
// CS0077.cs using System; class C { } struct S { } class M { public static void Main() { object o1, o2; C c; S s; o1 = new C(); o2 = new S(); s = o2 as S;  // CS0077, S is not a reference type. // try the following line instead // c = o1 as C; } }  
```