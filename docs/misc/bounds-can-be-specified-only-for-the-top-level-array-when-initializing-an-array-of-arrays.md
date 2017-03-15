---
title: "Les limites ne peuvent &#234;tre sp&#233;cifi&#233;es que pour le tableau de premier niveau lors de l’initialisation d’un tableau de tableaux | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32014"
  - "vbc32014"
helpviewer_keywords: 
  - "BC32014"
ms.assetid: d8d7155d-82d1-4a25-b9bb-1883e1586383
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les limites ne peuvent &#234;tre sp&#233;cifi&#233;es que pour le tableau de premier niveau lors de l’initialisation d’un tableau de tableaux
Une initialisation de tableau pour un tableau en escalier \(tableau de tableaux\) définit la longueur initiale de l’un des niveaux inférieurs. Vous pouvez spécifier uniquement la longueur du tableau de niveau supérieur dans l’instruction de déclaration de tableau.  
  
 **ID d’erreur :** BC32014  
  
### Pour corriger cette erreur  
  
1.  Supprimez la spécification de longueur de tous les tableaux sauf celui de niveau supérieur.  
  
2.  Définissez la longueur initiale des tableaux de niveau inférieur dans des instructions d’assignation ultérieures à l’aide du mot clé `New`.  
  
## Voir aussi  
 [NOTINBUILD Variable tableau](http://msdn.microsoft.com/fr-fr/c2da78bd-6928-46ba-805f-44f819dfaf93)   
 [NOTINBUILD Tableaux en escalier en Visual Basic](http://msdn.microsoft.com/fr-fr/05c12439-ee8f-4fef-ba75-b35402b67ab9)   
 [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator)