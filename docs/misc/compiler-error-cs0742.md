---
title: "Erreur du compilateur CS0742 | Microsoft Docs"
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
  - "CS0742"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0742"
ms.assetid: 078ee7af-17e4-4572-8fee-d97e09c9002b
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0742
Un corps de requête doit terminer par une clause select ou une clause group  
  
 Une expression de requête doit se terminer par une clause `select` ou une clause `group` sans continuation.  
  
### Pour corriger cette erreur  
  
1.  Ajoutez une [clause select](/dotnet/csharp/language-reference/keywords/select-clause) ou une [clause group](/dotnet/csharp/language-reference/keywords/group-clause) à la requête.  
  
## Exemple  
 Le code suivant génère l’erreur CS0742 :  
  
```  
// cs0742.cs using System.Linq; public class Test { public static int Main() { int[] array = { 1, 2, 3 }; var query = from num in array; // CS0742 return 1; } }  
```  
  
 Si la clause `group` utilise le mot clé [into](/dotnet/csharp/language-reference/keywords/into) pour stocker les résultats du regroupement dans un identificateur temporaire, elle ne peut pas être la dernière clause dans une requête. Une clause `select` ou une deuxième clause `group` est toujours exigée.  
  
## Voir aussi  
 [Expressions de requête \(LINQ\)](/dotnet/csharp/programming-guide/linq-query-expressions/index)