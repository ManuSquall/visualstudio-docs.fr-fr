---
title: "Erreur du compilateur CS0544 | Microsoft Docs"
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
  - "CS0544"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0544"
ms.assetid: f8230a02-a666-4a1a-94cb-46f87463206a
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0544
'substitution\_propriété' : substitution impossible, car 'non\_propriété' n’est pas une propriété  
  
 Vous avez tenté de substituer un type de données autre qu’une propriété en tant que [propriété](/dotnet/csharp/programming-guide/classes-and-structs/properties), ce qui n’est pas autorisé.  
  
 L’exemple suivant génère l’erreur CS0544 :  
  
```  
// CS0544.cs // compile with: /target:library public class a { public int i; } public class b : a { public override int i {   // CS0544 // try the following line instead // public new int i { get { return 0; } } }  
```