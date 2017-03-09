---
title: "Erreur du compilateur&#160;CS1951 | Microsoft Docs"
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
  - "CS1951"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1951"
ms.assetid: 799ba212-a000-44d9-b7da-a8c00eae63fa
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur&#160;CS1951
Une arborescence de l’expression lambda ne peut pas contenir un paramètre out ou ref  
  
 Une arborescence d’expression représente simplement des expressions en tant que structures de données. Il n’existe aucun moyen de représenter des emplacements de mémoire spécifiques, comme cela est nécessaire quand vous passez un paramètre par référence.  
  
### Pour corriger cette erreur  
  
1.  La seule option consiste à supprimer le modificateur `ref` dans la définition du délégué et à passer le paramètre par valeur.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1951 :  
  
```  
// cs1951.cs using System.Linq; public delegate int TestDelegate(ref int i); class Test { static void Main() { System.Linq.Expressions.Expression<TestDelegate> tree1 = (ref int x) => x; // CS1951 } }  
```  
  
## Voir aussi  
 [Arborescences d'expression](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)