---
title: "Erreur du compilateur CS0833 | Microsoft Docs"
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
  - "CS0833"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0833"
ms.assetid: 4ae32454-265f-47aa-bf2a-ee1d702330b7
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0833
Un type anonyme ne peut pas avoir plusieurs propriétés du même nom  
  
 Un type anonyme, comme tous les autres type, ne peut pas avoir deux propriétés du même nom.  
  
### Pour corriger cette erreur  
  
1.  Donnez un nom unique à chaque propriété du type.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0833 :  
  
```  
// cs0833.cs using System; public class C { public static int Main() { var c = new { p1 = 1, p1 = 2 }; // CS0833 return 1; } }  
```  
  
## Voir aussi  
 [Types anonymes](/dotnet/csharp/programming-guide/classes-and-structs/anonymous-types)