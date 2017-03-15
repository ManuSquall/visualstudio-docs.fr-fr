---
title: "Erreur du compilateur CS0716 | Microsoft Docs"
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
  - "CS0716"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0716"
ms.assetid: 806d25ef-f8a7-4c94-823e-e07904defcf4
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0716
Impossible de convertir en type static 'type'  
  
 Cette erreur se produit si votre code utilise un cast pour convertir un type static. Puisqu’un objet ne peut pas être une instance de type static, le cast d’un type static ne peut pas être significatif.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0716 :  
  
```  
// CS0716.cs public static class SC { static void F() { } } public class Test { public static void Main() { object o = new object(); System.Console.WriteLine((SC)o);  // CS0716 } }  
```