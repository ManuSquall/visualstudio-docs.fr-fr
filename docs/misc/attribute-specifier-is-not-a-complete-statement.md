---
title: "Le sp&#233;cificateur d’attribut n’est pas une instruction compl&#232;te | Microsoft Docs"
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
  - "vbc32035"
  - "bc32035"
helpviewer_keywords: 
  - "BC32035"
ms.assetid: a0ddd673-4170-4bea-9c22-777d7bf21dfd
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le sp&#233;cificateur d’attribut n’est pas une instruction compl&#232;te
Le spécificateur d’attribut n’est pas une instruction complète. Utilisez un signe de continuation de ligne pour appliquer l’attribut à l’instruction suivante.  
  
 Un bloc d’attributs apparaît seul sur une ligne de code source. Les attributs doivent être appliqués au début d’une instruction de déclaration, et ils doivent faire partie de cette instruction.  
  
 **ID d’erreur :** BC32035  
  
### Pour corriger cette erreur  
  
-   Si l’instruction de déclaration se trouve sur la ligne suivante, ajoutez un espace et un trait de soulignement \(`_`\) après le bloc d’attributs pour combiner les lignes de code source.  
  
-   Si aucune instruction de déclaration n’est associée au bloc d’attributs, fournissez\-en une ou supprimez le bloc d’attributs.  
  
-   Si l’attribut doit être appliqué à la totalité de l’assembly ou au module d’assembly actuel, le bloc d’attributs reste sur une ligne distincte du code source. Précédez le nom de l’attribut situé entre crochets angulaires \(`< >`\) de `Assembly:` ou de `Module:`, et n’ajoutez pas d’espace ni de trait de soulignement après le bloc d’attributs. Veillez également à que ce bloc d’attributs se trouve au début de votre fichier source.  
  
## Voir aussi  
 [NOT IN BUILD : Application des attributs](http://msdn.microsoft.com/fr-fr/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Procédure : diviser et combiner des instructions dans le code](../Topic/How%20to:%20Break%20and%20Combine%20Statements%20in%20Code%20\(Visual%20Basic\).md)