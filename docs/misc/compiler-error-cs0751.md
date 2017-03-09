---
title: "Erreur du compilateur CS0751 | Microsoft Docs"
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
  - "CS0751"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0751"
ms.assetid: 2ebaed5f-d3ca-452f-8fce-f3299b84360a
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0751
Une méthode partielle doit être déclarée au sein d’une classe partielle ou d’une structure partielle  
  
 Il n’est pas possible de déclarer une méthode [partielle](/dotnet/csharp/language-reference/keywords/partial-method), sauf si elle est encapsulée dans une classe partielle ou un struct partiel.  
  
### Pour corriger cette erreur  
  
1.  Vous pouvez soit supprimer le modificateur `partial` de la méthode et fournir une implémentation, soit ajouter le modificateur `partial` à la classe ou au struct englobant.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0751 :  
  
```  
// cs0751.cs using System; public class C { partial void Part(); // CS0751 public static int Main() { return 1; } }  
```  
  
## Voir aussi  
 [Classes et méthodes partielles](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)