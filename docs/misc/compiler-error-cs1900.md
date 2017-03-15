---
title: "Erreur du compilateur&#160;CS1900 | Microsoft Docs"
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
  - "CS1900"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1900"
ms.assetid: 08141138-bfea-4af3-a9a0-ec54cf2caa13
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur&#160;CS1900
Le niveau d'avertissement doit être compris entre 0 et 4  
  
 L’option du compilateur [\/warn](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option) peut uniquement prendre l’une des cinq valeurs possibles \(0, 1, 2, 3 ou 4\). Toute autre valeur passée à **\/warn** génère l’erreur CS1900.  
  
 L’exemple suivant génère l’erreur CS1900 :  
  
```  
// CS1900.cs // compile with: /W:5 // CS1900 expected class x { public static void Main() { } }  
```