---
title: "Erreur du compilateur CS1553 | Microsoft Docs"
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
  - "CS1553"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1553"
ms.assetid: aec64251-b4ac-45c0-b143-7ebda138af6e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1553
Déclaration non valide ; utilisez plutôt 'opérateur modificateur \<type\-destination\> \(...'  
  
 Le type de retour pour un [opérateur](/dotnet/csharp/language-reference/keywords/operator) doit précéder immédiatement la liste de paramètres, et le *modificateur* est soit `implicit`, soit **explicit**.  
  
 L’exemple suivant génère l’erreur CS1553 :  
  
```  
// CS1553.cs class MyClass { public static int implicit operator (MyClass f)   // CS1553 // try the following line instead // public static implicit operator int (MyClass f) { return 6; } public static void Main() { } }  
```