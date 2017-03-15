---
title: "Avertissement du compilateur&#160;(niveau&#160;1)&#160;CS1720 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1720"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1720"
ms.assetid: 97adc294-3a4c-4418-a4ed-ccff43125b62
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur&#160;(niveau&#160;1)&#160;CS1720
L’expression provoquera toujours un System.NullReferenceException, car la valeur par défaut de 'generic type' est null  
  
 Si vous écrivez une expression qui implique la valeur par défaut d’une variable de type générique correspondant à un type référence \(par exemple, une classe\), cette erreur se produit. Prenons l'expression suivante :  
  
```  
default(T).ToString()  
```  
  
 Étant donné que `T` est un type référence, sa valeur par défaut est Null ; par conséquent, si vous tentez de lui appliquer la méthode <xref:System.Object.ToString%2A>, cela lève une <xref:System.NullReferenceException>.  
  
## Exemple  
 La contrainte de référence de classe sur le type `T` garantit que `T` est un type référence.  
  
 L’exemple suivant génère l’avertissement CS1720.  
  
```  
// CS1720.cs using System; public class Tester { public static void GenericClass<T>(T t1) where T : class { Console.WriteLine(default(T).ToString());  // CS1720 } public static void Main() {} }  
```