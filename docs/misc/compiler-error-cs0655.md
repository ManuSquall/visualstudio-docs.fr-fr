---
title: "Erreur du compilateur CS0655 | Microsoft Docs"
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
  - "CS0655"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0655"
ms.assetid: 8ce340e2-eeeb-476a-8609-ab4bbaf10c44
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0655
'paramètre' n’est pas un argument d’attribut nommé valide, car il n’est pas un type de paramètre d’attribut valide  
  
 Consultez [Attributs](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md) pour en savoir plus sur les types de paramètres valides pour un attribut.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0655 :  
  
```  
// CS0655.cs using System; class MyAttribute : Attribute { // decimal is not valid attribute parameter type public decimal d = 0; public int e = 0; } [My(d = 0)]   // CS0655 // Try the following line instead: // [My(e = 0)] class C { public static void Main() { } }  
```