---
title: "Erreur du compilateur CS0153 | Microsoft Docs"
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
  - "CS0153"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0153"
ms.assetid: 3a0791e9-0ab9-4eaa-a230-d39aabaa9d5d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0153
Un goto case n'est valide qu'au sein d'une instruction switch  
  
 L’utilisateur a tenté d’utiliser la syntaxe des [commutateurs](/dotnet/csharp/language-reference/keywords/switch) en dehors d’une instruction **switch**. Pour plus d'informations, consultez [switch](/dotnet/csharp/language-reference/keywords/switch).  
  
 L’exemple suivant génère l’erreur CS0153 :  
  
```  
// CS0153.cs public class a { public static void Main() { goto case 5;   // CS0153 } }  
```