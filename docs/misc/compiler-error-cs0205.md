---
title: "Erreur du compilateur CS0205 | Microsoft Docs"
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
  - "CS0205"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0205"
ms.assetid: 616d98cf-e7a5-4f8e-93da-fcd6e1e4de35
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0205
Impossible d’appeler un membre de base abstrait : 'méthode'  
  
 Vous ne pouvez pas appeler une méthode [abstraite](/dotnet/csharp/language-reference/keywords/abstract), car elle n’a pas de corps de méthode. Pour plus d'informations, consultez [Classes abstract et sealed et membres de classe](/dotnet/csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members).  
  
 L’exemple suivant génère l’erreur CS0205 :  
  
```  
// CS0205.cs abstract public class MyClass { abstract public void M(); } public class MyClass2 : MyClass { public override void M() { base.M();   // CS0205, delete this line } public static void Main() { } }  
```