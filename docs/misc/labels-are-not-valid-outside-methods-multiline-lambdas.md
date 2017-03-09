---
title: "Les &#233;tiquettes ne sont pas valides en dehors des m&#233;thodes ou des expressions lambda multiligne | Microsoft Docs"
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
  - "vbc30016"
  - "bc30016"
helpviewer_keywords: 
  - "BC30016"
ms.assetid: 17d12a96-d759-4df9-882c-5e45c1d814a5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les &#233;tiquettes ne sont pas valides en dehors des m&#233;thodes ou des expressions lambda multiligne
Vous ne pouvez ajouter une étiquette à une instruction que dans une procédure `Sub``Function` et une procédure de propriété `Get` ou `Set`. Seules les instructions exécutables peuvent avoir une étiquette et toutes les instructions exécutables doivent se trouver à l’intérieur de procédures.  
  
 **ID d’erreur :** BC30016  
  
### Pour corriger cette erreur  
  
1.  Supprimez l’étiquette de l’instruction ou déplacez l’instruction dans une procédure.  
  
## Voir aussi  
 [How to: Label Statements](../Topic/How%20to:%20Label%20Statements%20\(Visual%20Basic\).md)   
 [Sub Statement](/dotnet/visual-basic/language-reference/statements/sub-statement)   
 [Function Statement](/dotnet/visual-basic/language-reference/statements/function-statement)   
 [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement)   
 [Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement)