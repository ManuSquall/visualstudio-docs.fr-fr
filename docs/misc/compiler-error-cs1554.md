---
title: "Erreur du compilateur CS1554 | Microsoft Docs"
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
  - "CS1554"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1554"
ms.assetid: 81e8d4ac-cdbf-4b75-8932-0bc271a8405c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1554
Déclaration non valide ; utilisez plutôt '\<type\> operator op \(...'  
  
 Le type de retour pour un [opérateur](/dotnet/csharp/language-reference/keywords/operator) défini par l’utilisateur doit figurer avant l’opérateur du mot clé.  
  
 L’exemple suivant génère l’erreur CS1554 :  
  
```  
// CS1554.cs class MyClass { public static operator ++ MyClass (MyClass f)    // CS1554 // try the following line instead // public static MyClass operator ++ (MyClass f) { return new MyClass (); } public static void Main() { } }  
```