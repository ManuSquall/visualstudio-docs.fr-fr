---
title: "Erreur du compilateur CS0678 | Microsoft Docs"
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
  - "CS0678"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0678"
ms.assetid: ca389fc9-da78-4e16-b68c-782f90b17c83
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0678
'variable' : un champ ne peut pas être à la fois volatile et readonly  
  
 Les mots clés [volatile](/dotnet/csharp/language-reference/keywords/volatile) et [readonly](/dotnet/csharp/language-reference/keywords/readonly) s’excluent mutuellement.  
  
 L’exemple suivant génère l’erreur CS0678 :  
  
```  
// CS0678.cs using System; class TestClass { private readonly volatile int i;   // CS0678 // try the following line instead // private volatile int i; public static void Main() { } }  
```