---
title: "Erreur du compilateur CS0715 | Microsoft Docs"
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
  - "CS0715"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0715"
ms.assetid: e3cd1e46-ccfa-4678-a2ed-69245f3558ba
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0715
'classe static' : les classes static ne peuvent pas contenir d’opérateurs définis par l’utilisateur  
  
 Les opérateurs définis par l’utilisateur opèrent sur des instances de classes. Les classes static ne pouvant pas être instanciées, il n’est pas possible de créer d’instances sur lesquelles les opérateurs peuvent agir. Par conséquent, les opérateurs définis par l’utilisateur ne sont pas autorisés pour les classes static.  
  
 L’exemple suivant génère l’erreur CS0715 :  
  
```  
// CS0715.cs public static class C { public static C operator+(C c)  // CS0715 { } public static void Main() { } }  
```