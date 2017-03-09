---
title: "Erreur du compilateur CS0745 | Microsoft Docs"
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
  - "CS0745"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0745"
ms.assetid: 6ae77eb2-a940-43aa-a198-3042d144613a
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0745
Mot clé contextuel 'by' attendu  
  
 Le modèle de la clause `group` est `group...by` suivi d’un `into` facultatif, comme illustré dans l’exemple suivant :  
  
```  
string[] names = { "Bob", "Bill", "Jonetta", "Mary" }; var query = from name in names group name by name[0];  
```  
  
 ou  
  
```  
var query2 = from name in names group name by name[0] into g //...additional query clauses  
```  
  
### Pour corriger cette erreur  
  
1.  Ajoutez le mot clé `by` à la clause `group`.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0745 :  
  
```  
// cs0745.cs using System; using System.Linq; public class C { public static int Main() { string[] names = { "Bob", "Bill", "Jonetta", "Mary" }; var query = from name in names group name name[0]; // CS0745 return 1; } }  
```  
  
## Voir aussi  
 [Expressions de requête \(LINQ\)](/dotnet/csharp/programming-guide/linq-query-expressions/index)   
 [group, clause](/dotnet/csharp/language-reference/keywords/group-clause)