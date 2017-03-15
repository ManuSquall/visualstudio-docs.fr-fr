---
title: "Erreur du compilateur CS1057 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1057"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1057"
ms.assetid: 6f247cfd-6d26-43b8-98d9-0a6d7c115cad
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1057
'member' : les classes statiques ne peuvent pas contenir de membres protégés  
  
 Cette erreur est générée par la déclaration d’un membre protégé à l’intérieur d’une classe statique.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1057.  
  
```  
// CS1057.cs using System; static class Class1 { protected static int x;   // CS1057 public static void Main() { } }  
```