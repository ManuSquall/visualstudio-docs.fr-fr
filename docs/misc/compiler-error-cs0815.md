---
title: "Erreur du compilateur CS0815 | Microsoft Docs"
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
  - "CS0815"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0815"
ms.assetid: 8f055d34-9ee4-482e-9e79-8b3698c55cb4
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0815
Impossible d’assigner 'expression' à une variable locale implicitement typée  
  
 Une expression utilisée comme initialiseur d’une variable implicitement typée doit avoir un type. Étant donné que les expressions de fonction anonyme, les expressions de groupe de méthode et l’expression de littéral null n’ont pas de type, elles ne constituent pas des initialiseurs appropriés. Une variable implicitement typée ne peut pas être initialisée avec une valeur null dans sa déclaration, mais une valeur null peut lui être assignée ultérieurement.  
  
### Pour corriger cette erreur  
  
1.  Fournissez un type explicite pour la variable.  
  
## Exemple  
 Le code suivant génère l’erreur CS0815 :  
  
```  
// cs0815.cs class Test { public static int Main() { var d = s => -1; // CS0815 var e = (string s) => 0; // CS0815 var p = null;//CS0815 var del = delegate(string a) { return -1; };// CS0815 return -1; } }  
```  
  
## Voir aussi  
 [Variables locales implicitement typées](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)