---
title: "Erreur du compilateur CS0758 | Microsoft Docs"
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
  - "CS0758"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0758"
ms.assetid: 06ddd548-1311-40db-9078-8a18107b8346
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0758
Soit les deux déclarations de méthode partielles utilisent un paramètre params, soit aucune des deux  
  
 Si une partie d’une méthode partielle spécifie un paramètre `params`, l’autre partie doit en spécifier un également.  
  
### Pour corriger cette erreur  
  
1.  Ajoutez le modificateur `params` dans une partie de la méthode ou supprimez\-le dans l’autre.  
  
## Exemple  
 Le code suivant génère l’erreur CS0758 :  
  
```  
using System; public partial class C { partial void Part(int i, params char[] array); partial void Part(int i, char[] array) // CS0758 { } public static int Main() { return 1; } }  
```  
  
## Voir aussi  
 [Classes et méthodes partielles](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)   
 [params](/dotnet/csharp/language-reference/keywords/params)