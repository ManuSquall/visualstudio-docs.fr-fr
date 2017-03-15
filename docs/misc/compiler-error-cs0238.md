---
title: "Erreur du compilateur CS0238 | Microsoft Docs"
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
  - "CS0238"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0238"
ms.assetid: 9b50c6e2-2c3f-431d-bdb7-557b0ec51626
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0238
'member' ne peut pas être sealed car il ne s’agit pas d’une substitution  
  
 [sealed](/dotnet/csharp/language-reference/keywords/sealed) a été utilisé sur un membre qui n’était pas marqué avec [override](/dotnet/csharp/language-reference/keywords/override). Pour plus d'informations, consultez [Héritage](/dotnet/csharp/programming-guide/classes-and-structs/inheritance).  
  
 L’exemple suivant génère l’erreur CS0238 :  
  
```  
// CS0238.cs abstract class MyClass { public abstract void f(); } class MyClass2 : MyClass { public static void Main() { } public sealed void f() // CS0238 // Try the following definition instead: // public override sealed void f() { } }  
```