---
title: "Erreur du compilateur CS0236 | Microsoft Docs"
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
  - "CS0236"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0236"
ms.assetid: 1522c421-744f-441f-9e05-6bb31311ab2a
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0236
Un initialiseur de champ ne peut pas faire référence au champ, à la méthode ou à la propriété non statique 'champ'  
  
 Les champs d’instance ne peuvent pas être utilisés pour initialiser d’autres champs d’instance en dehors d’une méthode. Si vous tentez d’initialiser une variable en dehors d’une méthode, envisagez d’effectuer l’initialisation dans le constructeur de classe. Pour plus d'informations, consultez [Méthodes](/dotnet/csharp/programming-guide/classes-and-structs/methods).  
  
 L’exemple suivant génère l’erreur CS0236 :  
  
```  
// CS0236.cs public class MyClass { public int i = 5; public int j = i;  // CS0236 public int k;      // initialize in constructor MyClass() { k = i; } public static void Main() { } }  
```