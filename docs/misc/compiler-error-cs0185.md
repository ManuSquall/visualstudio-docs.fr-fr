---
title: "Erreur du compilateur CS0185 | Microsoft Docs"
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
  - "CS0185"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0185"
ms.assetid: d6546e10-0af3-4860-8e6f-2da7dbeb3d28
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0185
'type' n’est pas un type référence requis par l’instruction lock  
  
 L’instruction [lock](/dotnet/csharp/language-reference/keywords/lock-statement) ne peut évaluer que des types référence. Pour plus d’informations, consultez [Synchronisation des threads](../Topic/Thread%20Synchronization%20\(C%23%20and%20Visual%20Basic\).md) et [Types référence](/dotnet/csharp/language-reference/keywords/reference-types).  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0185 :  
  
```  
// CS0185.cs public class MainClass { public static void Main () { lock (1)   // CS0185 // try the following lines instead // MainClass x = new MainClass(); // lock(x) { } } }  
```