---
title: "Les dimensions d’un tableau ne peuvent pas &#234;tre de taille n&#233;gative | Microsoft Docs"
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
  - "bc30611"
  - "vbc30611"
helpviewer_keywords: 
  - "BC30611"
ms.assetid: e310bd0d-f221-4b02-87f3-02124f4de87c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les dimensions d’un tableau ne peuvent pas &#234;tre de taille n&#233;gative
Une ou plusieurs limites de tableau spécifiées sont un nombre négatif. Vous pouvez spécifier un indice négatif seulement quand vous utilisez une limite supérieure de \-1 pour déclarer un tableau vide. Ce type de tableau n’a aucun élément, mais il n’a pas la valeur `Nothing`.  
  
 **ID d’erreur :** BC30611  
  
### Pour corriger cette erreur  
  
-   Remplacez la limite de tableau négative par un nombre positif.  
  
## Voir aussi  
 [Tableaux](/dotnet/visual-basic/programming-guide/language-features/arrays/index)