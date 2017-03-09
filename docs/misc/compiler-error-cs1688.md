---
title: "Erreur du compilateur CS1688 | Microsoft Docs"
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
  - "CS1688"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1688"
ms.assetid: e15672a1-2570-4e65-99fc-7acc190ae643
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1688
Impossible de convertir un bloc de méthode anonyme sans une liste de paramètres en type délégué 'délégué', car il a un ou plusieurs paramètres out  
  
 Dans la plupart des cas, le compilateur autorise l’omission des paramètres d’un bloc de méthode anonyme. Cette erreur se produit quand le bloc de méthode anonyme ne dispose pas d’une liste de paramètres alors que le délégué dispose d’un paramètre `out`. Le compilateur n’autorise pas cette situation, car cela reviendrait à ignorer la présence du paramètre `out`, ce qui n’est pas un comportement souhaitable.  
  
## Exemple  
 Le code suivant génère l’erreur CS1688.  
  
```  
// CS1688.cs using System; delegate void OutParam(out int i); class ErrorCS1676 { static void Main() { OutParam o; o = delegate  // CS1688 // Try this instead: // o = delegate(out int i) { Console.WriteLine(""); }; } }  
```