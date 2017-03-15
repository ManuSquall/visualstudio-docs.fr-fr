---
title: "Erreur du compilateur CS1012 | Microsoft Docs"
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
  - "CS1012"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1012"
ms.assetid: 4acc5fe0-da47-4882-b7d8-557767d7cf03
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1012
Trop de caractères dans le littéral de caractère  
  
 L’utilisateur a tenté d’initialiser une constante [char](/dotnet/csharp/language-reference/keywords/char) avec plusieurs caractères.  
  
 L’erreur CS1012 peut également se produire lors de la liaison de données. Par exemple, la ligne suivante génère une erreur :  
  
 `<%# DataBinder.Eval(Container.DataItem, 'doctitle') %>`  
  
 Essayez plutôt la ligne suivante :  
  
 `<%# DataBinder.Eval(Container.DataItem, "doctitle") %>`  
  
 L’exemple suivant génère l’erreur CS1012 :  
  
```  
// CS1012.cs class Sample { static void Main() { char a = 'xx';   // CS1012 char a2 = 'x';   // OK System.Console.WriteLine(a2); } }  
```