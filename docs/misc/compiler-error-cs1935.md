---
title: "Erreur du compilateur CS1935 | Microsoft Docs"
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
  - "CS1935"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1935"
ms.assetid: d5dda801-fbf3-4340-bfe1-f9409f2d344d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1935
Impossible de trouver une implémentation du modèle de requête pour le type source 'type'. 'méthode' introuvable. Vous manque\-t\-il une référence à 'System.Core.dll' ou une directive using pour 'System.Linq' ?  
  
 Le type source dans une requête doit être `IEnumerable`, `IEnumerable<T>` ou un type dérivé, ou un type pour lequel vous\-même ou quelqu’un d’autre avez implémenté les opérateurs de requête standard. Si le type source est un `IEnumerable` ou `IEnumerable<T>`, vous devez ajouter une référence à system.core.dll et une directive `using` pour l’espace de noms System.Linq pour que les méthodes d’extension d’opérateur de requête standard soient dans la portée. Les implémentations personnalisées des opérateurs de requête standard doivent être mises dans la portée de la même façon, avec une directive `using` et, si nécessaire, une référence à l’assembly.  
  
### Pour corriger cette erreur  
  
1.  Ajoutez les directives using et les références nécessaires au projet.  
  
## Exemple  
 Le code suivant génère l’erreur CS1935, car la directive `using` pour System.Linq est commentée :  
  
```  
// cs1935.cs // CS1935 using System; using System.Collections.Generic; // using System.Linq; class Test { static int Main() { int[] nums = {0,1,2,3,4,5}; IEnumerable<int> e = from n in nums where n > 3 select n; return 0; } }  
```  
  
## Voir aussi  
 [Standard Query Operators Overview](../Topic/Standard%20Query%20Operators%20Overview.md)