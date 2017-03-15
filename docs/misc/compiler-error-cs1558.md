---
title: "Erreur du compilateur CS1558 | Microsoft Docs"
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
  - "CS1558"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1558"
ms.assetid: ee603d66-007e-4782-9285-7ff031975f0f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1558
'class' ne dispose pas d’une méthode Main static appropriée  
  
 L’option du compilateur [\/main](/dotnet/csharp/language-reference/compiler-options/main-compiler-option) a spécifié une classe dans laquelle rechercher une méthode **Main**. Toutefois, la méthode [Main](/dotnet/csharp/programming-guide/main-and-command-args/main-and-command-line-arguments) n’était pas définie correctement.  
  
 L’exemple suivant génère l’erreur CS1558 en raison d’un type de retour non valide.  
  
```  
// CS1558.cs // compile with: /main:MyNamespace.MyClass namespace MyNamespace { public class MyClass { public static float Main() { return 0.0; // CS1558 because the return type is a float. } } }  
```