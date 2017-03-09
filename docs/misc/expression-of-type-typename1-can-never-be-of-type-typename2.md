---
title: "L’expression de type &#39;&lt;nom_type1&gt;&#39; ne peut pas &#234;tre de type &#39;&lt;nom_type2&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31430"
  - "bc31430"
helpviewer_keywords: 
  - "BC31430"
ms.assetid: 1d527033-3f6f-4945-b1d3-5ef59a1e1b53
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’expression de type &#39;&lt;nom_type1&gt;&#39; ne peut pas &#234;tre de type &#39;&lt;nom_type2&gt;&#39;
Une expression `TypeOf`...`Is` teste une variable de référence d’objet sur un type de données qu’elle ne peut pas contenir.  
  
 Dans certains cas, le compilateur peut déterminer qu’un test `TypeOf`...`Is` ne peut qu’échouer, par exemple s’il n’y a aucune relation d’héritage entre deux classes.  
  
 Le code suivant peut générer cette erreur.  
  
 `Dim refVar as System.Windows.Forms.Form`  
  
 `If TypeOf refVar Is System.Array`  
  
 `End If`  
  
 <xref:System.Windows.Forms.Form> et <xref:System.Array> étant des types sans aucune relation entre eux, le compilateur peut déterminer que l’expression `TypeOf`...`Is` retourne `False` pour toutes les valeurs de `refVar`.  
  
 **ID d’erreur :** BC31430  
  
### Pour corriger cette erreur  
  
-   Testez la variable pour un type de données réaliste ou supprimez complètement le test `TypeOf`...`Is`.  
  
## Voir aussi  
 [TypeOf Operator](/dotnet/visual-basic/language-reference/operators/typeof-operator)   
 [How to: Determine What Type an Object Variable Refers To](../Topic/How%20to:%20Determine%20What%20Type%20an%20Object%20Variable%20Refers%20To%20\(Visual%20Basic\).md)