---
title: "Impossible de convertir l’expression lambda en &#39;&lt;nom_type&gt;&#39;, car &#39;&lt;nom_type&gt;&#39; n’est pas un type d&#233;l&#233;gu&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36625"
  - "vbc36625"
helpviewer_keywords: 
  - "BC36625"
ms.assetid: c03634d4-d831-4f8c-b6ab-566465968e4d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible de convertir l’expression lambda en &#39;&lt;nom_type&gt;&#39;, car &#39;&lt;nom_type&gt;&#39; n’est pas un type d&#233;l&#233;gu&#233;
Les expressions lambda peuvent être utilisées là où les délégués sont valides. Elles peuvent être uniquement converties en types délégués compatibles. Par exemple, vous pouvez définir un type délégué et lui assigner une expression lambda ou envoyer une expression lambda en tant qu’argument à un paramètre <xref:System.Func%601>. Ces exemples sont présentés dans le code suivant.  
  
```vb#  
Module Module1 Delegate Function FunDel(ByVal m As Integer) As Boolean Sub Main() ' Assign a lambda expression to a function delegate. Dim negative As FunDel = Function(n As Integer) n < 0 Console.WriteLine(negative(-3)) ' Send a lambda as the argument to a delegate parameter. Dim numbers() As Integer = {3, 4, 2, 8, 1, 0, 9, 13, 42} Dim evens = numbers.Where(Function(n) n Mod 2 = 0) For Each even In evens Console.WriteLine(even) Next End Sub End Module  
```  
  
 **ID d’erreur :** BC36625  
  
## Voir aussi  
 [Lambda Expressions](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)