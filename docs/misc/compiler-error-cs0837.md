---
title: "Erreur du compilateur CS0837 | Microsoft Docs"
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
  - "CS0837"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0837"
ms.assetid: cbde45dc-222c-4bfe-8814-856476319d37
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0837
Le premier opérande d’un opérateur « is » ou « as » ne peut pas être une expression lambda ou une méthode anonyme.  
  
 Les expressions lambda et les méthodes anonymes ne peuvent pas être utilisées du côté gauche d’un opérateur [is](/dotnet/csharp/language-reference/keywords/is) ou [as](/dotnet/csharp/language-reference/keywords/as).  
  
### Pour corriger cette erreur  
  
-   Si l’erreur implique l’opérateur `is`, n’oubliez pas que `is` prend une valeur et un type, puis vous indique si la valeur peut être transformée en ce type par une conversion de référence, boxing ou unboxing. Étant donné que les expressions lambda ne sont pas des valeurs et qu’elles n’ont aucune conversion de référence, boxing ou unboxing, elles ne sont pas candidates pour `is`.  
  
-   Si le code utilise incorrectement `as`, la correction consiste probablement à le transformer en cast.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0837 :  
  
```  
// cs0837.cs namespace TestNamespace { public delegate void Del(); class Test { static int Main() { bool b1 = (() => { }) is Del;   // CS0837 bool b2 = delegate() { } is Del;// CS0837 Del d1 = () => { } as Del;      // CS0837 Del d2 = delegate() { } as Del; // CS0837 return 1; } } }  
```