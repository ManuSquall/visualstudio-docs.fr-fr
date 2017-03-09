---
title: "&#39;Group&#39; n’est pas autoris&#233; dans ce contexte&#160;; identificateur attendu | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36708"
  - "vbc36708"
helpviewer_keywords: 
  - "BC36708"
ms.assetid: ef6b453e-68e7-47c2-997c-9fd1ca074217
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Group&#39; n’est pas autoris&#233; dans ce contexte&#160;; identificateur attendu
Le mot clé `Group` est inclus dans la section `Into` d’une clause `Aggregate`. Le mot clé `Group` est valide uniquement dans les clauses `Group By` ou `Group Join`.  
  
 **ID d’erreur :** BC36618  
  
### Pour corriger cette erreur  
  
-   Supprimez le mot clé `Group` de la clause `Aggregate`. Vous pouvez ajouter une clause `Group By` à la requête pour regrouper les résultats.  
  
## Voir aussi  
 [Aggregate Clause](/dotnet/visual-basic/language-reference/queries/aggregate-clause)   
 [Group By, clause](/dotnet/visual-basic/language-reference/queries/group-by-clause)   
 [Group Join Clause](/dotnet/visual-basic/language-reference/queries/group-join-clause)   
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)