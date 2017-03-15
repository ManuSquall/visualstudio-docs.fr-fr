---
title: "Erreur du compilateur CS0182 | Microsoft Docs"
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
  - "CS0182"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0182"
ms.assetid: a9e97bb8-f06e-499f-aadf-26abc2082f98
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0182
Un argument d'attribut doit être une expression constante, une expression typeof ou une expression de création de tableau d'un type de paramètre d'attribut  
  
 Certaines restrictions s’appliquent à l’utilisation de certains types d’arguments avec des attributs. Notez que, outre les restrictions spécifiées dans le message d’erreur, les types suivants ne sont pas autorisés en tant qu’arguments d’attribut :  
  
-   [sbyte](/dotnet/csharp/language-reference/keywords/sbyte)  
  
-   [ushort](/dotnet/csharp/language-reference/keywords/ushort)  
  
-   [uint](/dotnet/csharp/language-reference/keywords/uint)  
  
-   [ulong](/dotnet/csharp/language-reference/keywords/ulong)  
  
-   [decimal](/dotnet/csharp/language-reference/keywords/decimal)  
  
 Pour plus d’informations, consultez [NOT IN BUILD : Attributs globaux \(Guide de programmation C\#\)](http://msdn.microsoft.com/fr-fr/7c6c41f8-f0d5-4345-8987-3d91f9bae136).  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0182 :  
  
```  
// CS0182.cs public class MyClass { static string s = "Test"; [System.Diagnostics.ConditionalAttribute(s)]   // CS0182 // try the following line instead // [System.Diagnostics.ConditionalAttribute("Test")] void NonConstantArgumentToConditional() { } public static void Main() { } }  
```