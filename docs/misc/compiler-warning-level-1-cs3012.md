---
title: "Avertissement du compilateur (niveau&#160;1) CS3012 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS3012"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3012"
ms.assetid: 1f7555b4-61e4-4821-85c9-586301df4c5c
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;1) CS3012
Vous ne pouvez pas spécifier l'attribut CLSCompliant sur un module qui diffère de l'attribut CLSCompliant de l'assembly  
  
 Afin qu’un module soit conforme à la spécification CLS \(Common Language Specification\) via `[module:System.CLCSompliant(true)]`, il doit être généré avec l’option [\/target:module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md) du compilateur. Pour plus d’informations sur la spécification CLS, consultez [Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Exemple  
 L’exemple suivant, quand il est généré sans `/target:module`, génère l’erreur CS3012 :  
  
```  
// CS3012.cs // compile with: /W:1 [module:System.CLSCompliant(true)]   // CS3012 public class C { public static void Main() { } }  
```