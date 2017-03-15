---
title: "Erreur du compilateur CS0753 | Microsoft Docs"
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
  - "CS0753"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0753"
ms.assetid: 287dd9da-da74-4290-9fa1-21ef1a8150fe
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0753
Seules les méthodes, classes, structs ou interfaces peuvent être partielles.  
  
 Le modificateur [partial](/dotnet/csharp/language-reference/keywords/partial-type) ne peut être utilisé qu’avec des classes, structs, interfaces et méthodes.  
  
### Pour corriger cette erreur  
  
1.  Supprimez le modificateur `partial` de la variable ou de la construction de langage.  
  
## Exemple  
 Le code suivant génère l’erreur CS0753 :  
  
```  
// cs0753.cs using System; public partial class C { partial int num; // CS0753 public static int Main() { return 1; } }  
```  
  
## Voir aussi  
 [Classes et méthodes partielles](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)