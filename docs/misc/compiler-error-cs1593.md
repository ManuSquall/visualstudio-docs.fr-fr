---
title: "Erreur du compilateur CS1593 | Microsoft Docs"
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
  - "CS1593"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1593"
ms.assetid: 7476e799-8a8d-457d-b4e7-2d5e073799d8
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1593
Le délégué 'del' ne prend pas les arguments 'nombre'  
  
 Le nombre d’arguments passés à un appel de [délégué](/dotnet/csharp/language-reference/keywords/delegate) ne correspond pas au nombre de paramètres dans la déclaration du délégué.  
  
 L’exemple suivant génère l’avertissement CS1593 :  
  
```  
// CS1593.cs using System; delegate string func(int i);   // declare delegate class a { public static void Main() { func dt = new func(z); x(dt); } public static string z(int j) { Console.WriteLine(j); return j.ToString(); } public static void x(func hello) { hello(8, 9);   // CS1593 // try the following line instead // hello(8); } }  
```