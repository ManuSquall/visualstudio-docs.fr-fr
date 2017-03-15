---
title: "Erreur du compilateur CS0241 | Microsoft Docs"
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
  - "CS0241"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "valeurs de paramètre de méthode par défaut"
  - "par défaut, valeurs de paramètre"
  - "par défaut, valeurs de paramètre de méthode"
  - "valeurs de paramètre par défaut"
  - "CS0241"
ms.assetid: be31b194-3de5-4aab-b23a-6cf790f940ab
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0241
Les spécificateurs de paramètres par défaut ne sont pas autorisés  
  
 Les [paramètres de méthode](/dotnet/csharp/language-reference/keywords/method-parameters) ne peuvent pas avoir de valeurs par défaut. Utilisez des surcharges de méthode pour obtenir le même effet. Pour plus d'informations, consultez [Passage de paramètres](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0241 : En outre, l’exemple montre comment simuler, avec la surcharge, une méthode avec des arguments par défaut.  
  
```  
// CS0241.cs public class A { public void Test(int i = 9) {}   // CS0241 } public class B { public void Test() { Test(9); } public void Test(int i)  {} } public class C { public static void Main() { B x = new B(); x.Test(); } }  
```