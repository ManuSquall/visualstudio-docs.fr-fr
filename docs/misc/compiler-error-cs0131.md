---
title: "Erreur du compilateur CS0131 | Microsoft Docs"
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
  - "CS0131"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0131"
ms.assetid: 822852cc-a426-4b7d-b2ff-0026a0c0a0e7
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0131
La partie gauche d'une assignation doit être une variable, une propriété ou un indexeur  
  
 Dans une instruction d’assignation, la valeur de la partie droite est assignée à la partie gauche. La partie gauche doit être une variable, une propriété ou un indexeur.  
  
 Pour corriger cette erreur, vérifiez que tous les opérateurs sont dans la partie droite et que la partie gauche correspond à une variable, une propriété ou un indexeur. Pour plus d’informations, consultez [Instructions, expressions et opérateurs](/dotnet/csharp/programming-guide/statements-expressions-operators/index).  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0131.  
  
```  
// CS0131.cs public class MyClass { public int i = 0; public void MyMethod() { i++ = 1;   // CS0131 // try the following line instead // i = 1; } public static void Main() { } }  
```  
  
## Exemple  
 Cette erreur peut également se produire si vous essayez d’exécuter des opérations arithmétiques dans la partie gauche d’un opérateur d’assignation, comme dans l’exemple suivant.  
  
```  
// CS0131b.cs public class C { public static int Main() { int a = 1, b = 2, c = 3; if (a + b = c) // CS0131 // try this instead // if (a + b == c) return 0; return 1; } }  
```