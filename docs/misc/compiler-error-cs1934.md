---
title: "Erreur du compilateur CS1934 | Microsoft Docs"
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
  - "CS1934"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1934"
ms.assetid: 18624be3-d534-4695-bafd-cc664fcde15e
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1934
Impossible de trouver une implémentation du modèle de requête pour le type source 'type'. 'méthode' introuvable. Spécifiez explicitement le type de la variable de portée 'nom'.  
  
 Cette erreur se produit si une expression de requête spécifie une source de données pour laquelle aucun opérateur de requête standard n’est implémenté. Une façon de générer cette erreur est de spécifier un `ArrayList` sans indiquer de type explicite pour la variable de portée.  
  
### Pour corriger cette erreur  
  
1.  Dans l’exemple suivant, la solution consiste simplement à spécifier le type de la variable de portée :  
  
    ```  
    var q = from int x in list  
    ```  
  
## Exemple  
 L’exemple suivant illustre une façon de générer l’erreur CS1934 :  
  
```  
// cs1934.cs using System.Linq; using System.Collections; static class Test { public static void Main() { var list = new ArrayList { 0, 1, 2, 3, 4, 5 }; var q = from x in list // CS1934 select x + 1; } }  
```  
  
## Voir aussi  
 [How to: Query an ArrayList with LINQ](../Topic/How%20to:%20Query%20an%20ArrayList%20with%20LINQ.md)