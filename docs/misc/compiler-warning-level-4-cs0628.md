---
title: "Avertissement du compilateur (niveau&#160;4) CS0628 | Microsoft Docs"
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
  - "CS0628"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0628"
ms.assetid: a54cfad8-27c9-4abb-8c83-982615489a10
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;4) CS0628
'membre' : nouveau membre protected déclaré dans une classe sealed  
  
 Une classe [sealed](/dotnet/csharp/language-reference/keywords/sealed) ne peut pas introduire un membre [protected](/dotnet/csharp/language-reference/keywords/protected), car aucune autre classe ne pourra hériter de la classe `sealed`et utiliser le membre `protected`.  
  
 L’exemple suivant génère l’erreur CS0628 :  
  
```  
// CS0628.cs // compile with: /W:4 sealed class C { protected int i;   // CS0628 } class MyClass { public static void Main() { } }  
```