---
title: "Erreur du compilateur CS0081 | Microsoft Docs"
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
  - "CS0081"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0081"
ms.assetid: a5649abc-89ea-4f64-8c3c-eb36df926561
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0081
La déclaration du paramètre de type doit être un identificateur et non un type  
  
 Quand vous déclarez une méthode ou un type générique, spécifiez le paramètre de type comme identificateur, par exemple « T » ou « inputType ». Quand le code client appelle la méthode, il fournit le type, qui remplace chaque occurrence de l’identificateur dans le corps de la méthode ou de la classe. Pour plus d'informations, consultez [Paramètres de type générique](/dotnet/csharp/programming-guide/generics/generic-type-parameters).  
  
```  
// CS0081.cs class MyClass { public void F<int>() {}   // CS0081 public void F<T>(T input) {}   // OK public static void Main() { MyClass a = new MyClass(); a.F<int>(2); a.F<double>(.05); } }  
```  
  
## Voir aussi  
 [Génériques](/dotnet/csharp/programming-guide/generics/index)