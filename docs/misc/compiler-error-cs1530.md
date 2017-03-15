---
title: "Erreur du compilateur CS1530 | Microsoft Docs"
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
  - "CS1530"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1530"
ms.assetid: 3844b5ef-e0ec-42df-9267-72689020f128
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1530
Le mot clé 'new' n'est pas autorisé dans les éléments définis dans un espace de noms  
  
 Il n’est pas utile de spécifier le mot clé [new](/dotnet/csharp/language-reference/keywords/new) sur une construction qui se trouve dans un [espace de noms](/dotnet/csharp/language-reference/keywords/namespace).  
  
 L’exemple suivant génère l’erreur CS1530 :  
  
```  
// CS1530.cs namespace a { new class i   // CS1530 { } // try the following instead class ii { public static void Main() { } } }  
```