---
title: "Avertissement du compilateur (niveau&#160;3) CS1718 | Microsoft Docs"
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
  - "CS1718"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1718"
ms.assetid: 7c1c11fd-4f91-482d-b8f7-efe2a361634e
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;3) CS1718
Comparaison effectuée avec la même variable ; souhaitiez\-vous comparer autre chose ?  
  
 Si vous voulez comparer autre chose, il vous suffit de corriger l’instruction.  
  
 Mais il est également possible que vous vouliez tester les valeurs true et false à l’aide d’instructions telles que `if (a == a) (true)` ou `if (a < a) (false)`. Il est préférable d’utiliser `if (true)` ou `if (false)`. Il existe deux raisons à cela :  
  
-   C’est plus simple : pour être clair, il vaut mieux rester simple.  
  
-   Cela permet d’éviter toute confusion : les types valeur Nullable sont une nouveauté de C\# 2.0 et sont similaires à la valeur `null` de T\-SQL, le langage de programmation utilisé par SQL Server. Les développeurs qui connaissent T\-SQL peuvent s’inquiéter de l’effet des types Nullable dans des expressions telles que `if (a == a)`, car cela implique l’utilisation de la logique ternaire dans T\-SQL. Si vous utilisez `true` ou `false`, vous évitez toute confusion.  
  
## Exemple  
 Le code suivant génère l’avertissement CS1718.  
  
```  
// CS1718.cs using System; public class Tester { public static void Main() { int i = 0; if (i == i) { // CS1718.cs //if (true) { i++; } } }  
```