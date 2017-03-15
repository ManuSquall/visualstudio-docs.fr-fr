---
title: "Avertissement du compilateur (niveau&#160;4) CS0028 | Microsoft Docs"
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
  - "CS0028"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0028"
ms.assetid: 47df919f-01fa-45ae-a4b7-912445e679e2
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;4) CS0028
'déclaration\_fonction' possède une signature erronée pour un point d’entrée  
  
 La déclaration de méthode pour `Main` n’est pas valide : elle a été déclarée avec une signature non valide.`Main` doit être déclarée comme static et doit retourner [int](/dotnet/csharp/language-reference/keywords/int) ou [void](/dotnet/csharp/language-reference/keywords/void). Pour plus d'informations, consultez [Main\(\) et arguments de ligne de commande](/dotnet/csharp/programming-guide/main-and-command-args/main-and-command-line-arguments).  
  
 L’exemple suivant génère l’erreur CS0028 :  
  
```  
// CS0028.cs // compile with: /W:4 /warnaserror public class a { public static double Main(int i)   // CS0028 // Try the following line instead: // public static void Main() { } }  
```