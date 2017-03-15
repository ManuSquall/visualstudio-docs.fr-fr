---
title: "Erreur du compilateur CS0180 | Microsoft Docs"
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
  - "CS0180"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0180"
ms.assetid: a21bf0a2-ed5a-4ddd-88d3-240babc5888a
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0180
'membre' ne peut pas être à la fois extern et abstract  
  
 Les mots clés [abstract](/dotnet/csharp/language-reference/keywords/abstract) et [extern](/dotnet/csharp/language-reference/keywords/extern) s’excluent mutuellement. Le mot clé `extern` signifie que le membre est défini en dehors du fichier, et **abstract** signifie que l’implémentation est fournie dans une classe dérivée. Pour plus d’informations, consultez [Méthodes](/dotnet/csharp/programming-guide/classes-and-structs/methods).  
  
 L’exemple suivant génère l’erreur CS0180 :  
  
```  
// CS0180.cs namespace MyNamespace { public class MyClass { public extern abstract int Foo(int a);   // CS0180 public static void Main() { } } }  
```