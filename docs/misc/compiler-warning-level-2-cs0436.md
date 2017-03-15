---
title: "Avertissement du compilateur (niveau&#160;2) CS0436 | Microsoft Docs"
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
  - "CS0436"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0436"
ms.assetid: c4135d9d-3511-4bbc-9540-48c2091f869c
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;2) CS0436
Le type 'type' dans 'assembly' est en conflit avec le type importé 'type2' dans 'assembly'. Utilisation du type défini dans 'assembly'.  
  
 Cet avertissement est émis quand un type dans un fichier source \(fichier\_2\) est en conflit avec un type importé dans fichier\_1. Le compilateur utilise celui figurant dans le fichier source.  
  
## Exemple  
  
```  
// CS0436_a.cs // compile with: /target:library public class A { public void Test() { System.Console.WriteLine("CS0436_a"); } }  
```  
  
## Exemple  
 L’exemple suivant génère l’avertissement CS0436.  
  
```  
// CS0436_b.cs // compile with: /reference:CS0436_a.dll // CS0436 expected public class A { public void Test() { System.Console.WriteLine("CS0436_b"); } } public class Test { public static void Main() { A x = new A(); x.Test(); } }  
```