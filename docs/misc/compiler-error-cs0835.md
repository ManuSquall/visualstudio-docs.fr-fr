---
title: "Erreur du compilateur CS0835 | Microsoft Docs"
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
  - "CS0835"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0835"
ms.assetid: 593c26f6-6d82-49a6-8ace-4d29dd9f5fbe
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0835
Impossible de convertir une expression lambda en une arborescence d’expression dont l’argument de type 'type' n’est pas un type délégué.  
  
 Si une expression lambda est convertie en une arborescence d’expression, elle doit disposer d’un type délégué pour son argument. De plus, l’expression lambda doit pouvoir être convertie en type délégué.  
  
### Pour corriger cette erreur  
  
1.  Remplacez le paramètre de type `int` par un type délégué, par exemple `Func<int,int>`.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0835 :  
  
```  
// cs0835.cs using System; using System.Linq; using System.Linq.Expressions; public class C { public static int Main() { Expression<int> e = x => x + 1; // CS0835 // Try the following line instead. // Expression<Func<int,int>> e2 = x => x + 1; return 1; } }  
```