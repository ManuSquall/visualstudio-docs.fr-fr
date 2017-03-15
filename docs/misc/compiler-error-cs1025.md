---
title: "Erreur du compilateur CS1025 | Microsoft Docs"
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
  - "CS1025"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1025"
ms.assetid: 491c186f-cb40-47a9-9656-44fadfa18ae2
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1025
Commentaire sur une seule ligne ou fin de ligne attendue  
  
 Une ligne contenant une [directive de préprocesseur](/dotnet/csharp/language-reference/preprocessor-directives/index) ne peut pas avoir de commentaires multilignes.  
  
 L’exemple suivant génère l’erreur CS1025 :  
  
```  
#if true /* hello */   // CS1025 #endif   // this is a good comment  
```  
  
 L’erreur CS1025 peut également se produire si vous tentez d’utiliser une directive de préprocesseur non valide, comme dans l’exemple suivant :  
  
```  
// CS1025.cs #define a class Sample { static void Main() { #if a 1   // CS1025, invalid syntax System.Console.WriteLine("Hello, World!"); #endif } }  
```