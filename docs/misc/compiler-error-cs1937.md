---
title: "Erreur du compilateur CS1937 | Microsoft Docs"
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
  - "CS1937"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1937"
ms.assetid: f13e8dc9-8c20-477e-8b74-7192848e08a2
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1937
Le nom 'nom' n’est pas dans la portée à gauche de 'equals'. Échangez les expressions de chaque côté de 'equals'.  
  
 Le mot clé `equals` est un opérateur spécial utilisé dans une clause `join` pour déterminer l’égalité entre deux expressions. La variable de portée pour la séquence source gauche est dans la portée à gauche du signe égal, et la variable de portée pour la source droite est uniquement dans la portée à gauche du signe égal. Vous pouvez le vérifier en testant IntelliSense dans l’exemple de code suivant.  
  
### Pour corriger cette erreur  
  
1.  Permutez les deux variables de portée, comme indiqué dans la ligne commentée de l’exemple suivant :  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1937.  
  
```  
// cs1937.cs using System.Linq; class Test { static void Main() { int[] sourceA = { 1, 2, 3, 4, 5 }; int[] sourceB = { 3, 4, 5, 6, 7 }; var query = from a in sourceA join b in sourceB on b equals a // CS1937 // Try the following line instead. //join b in sourceB on a equals b select new { a, b }; } }  
```  
  
 Le côté gauche est généralement appelé le côté « externe » et le droit est généralement appelé le côté « interne ».  
  
## Voir aussi  
 [join, clause](/dotnet/csharp/language-reference/keywords/join-clause)