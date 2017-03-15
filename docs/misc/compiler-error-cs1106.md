---
title: "Erreur du compilateur&#160;CS1106 | Microsoft Docs"
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
  - "CS1106"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1106"
ms.assetid: 3585600a-6b2c-47aa-a418-ef049f07c107
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur&#160;CS1106
Les méthodes d’extension doivent être définies dans une classe statique non générique.  
  
 Les méthodes d’extension doivent être définies en tant que méthodes statiques dans une classe statique non générique.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1106, car la classe `Extensions` n’est pas définie en tant que `static` :  
  
```  
// cs1106.cs public class Extensions // CS1106 { public  static void Test<T>(this System.String s) {} }  
```  
  
## Voir aussi  
 [Méthodes d'extension](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)   
 [statiques](/dotnet/csharp/language-reference/keywords/static)