---
title: "Erreur du compilateur CS0527 | Microsoft Docs"
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
  - "CS0527"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0527"
ms.assetid: 1acd244b-c55b-424f-b038-a130d65b8685
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0527
Le type 'type' qui figure dans la liste des interfaces n’est pas une interface  
  
 Il est possible pour un [struct](/dotnet/csharp/language-reference/keywords/struct) ou une [interface](/dotnet/csharp/language-reference/keywords/interface) d’hériter d’une autre interface, mais pas à partir de n’importe quel autre type.  
  
 L’exemple suivant génère l’erreur CS0527 :  
  
```  
// CS0527.cs // compile with: /target:library public struct clx : int {}   // CS0527 int not an interface  
```