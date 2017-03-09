---
title: "Erreur du compilateur CS1940 | Microsoft Docs"
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
  - "CS1940"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1940"
ms.assetid: 546e9bba-725d-4ea9-826f-37ec9d832add
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1940
Plusieurs implémentations du modèle de requête ont été trouvées pour le type source 'type'. Appel ambigu à 'méthode'.  
  
 Cette erreur est générée quand plusieurs implémentations d’une méthode de requête sont définies et que le compilateur ne parvient pas à déterminer celle qu’il convient d’utiliser pour la requête. Dans l’exemple suivant, les deux versions de `Select` ont la même signature, car les deux acceptent un `int` comme paramètre d’entrée et ont `int` comme valeur de retour.  
  
### Pour corriger cette erreur  
  
1.  Fournissez une seule implémentation pour chaque méthode.  
  
## Exemple  
 Le code suivant génère l’erreur CS1940 :  
  
```  
// cs1940.cs using System; //must include explicitly for types defined in 3.5 class Test { public delegate int Dele(int x); int num = 0; public int Select(Func<int, int> d) { return d(this.num); } public int Select(Dele d) // CS1940 { return d(this.num) + 1; } public static void Main() { var q = from x in new Test() select x; } }  
```  
  
## Voir aussi  
 [Standard Query Operators Overview](../Topic/Standard%20Query%20Operators%20Overview.md)