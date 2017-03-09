---
title: "La plage sp&#233;cifi&#233;e pour l’instruction &#39;Case&#39; n’est pas valide | Microsoft Docs"
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
  - "vbc40052"
  - "bc40052"
helpviewer_keywords: 
  - "BC40052"
ms.assetid: a11d92f6-dc13-46a0-a8ca-5a962a0ed968
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La plage sp&#233;cifi&#233;e pour l’instruction &#39;Case&#39; n’est pas valide
Une plage non valide a été spécifiée pour une instruction `Case`.  
  
 Quand vous comparez la même expression à plusieurs valeurs différentes, vous pouvez utiliser les instructions `Select...Case` comme alternatives aux instructions `If...Then...Else`. Les instructions `If` et `ElseIf` évaluent une expression différente dans chaque instruction, alors que l’instruction `Select` évalue une même expression une seule fois, puis l’utilise pour chaque comparaison. Chaque instruction `Case` peut contenir plusieurs valeurs, une plage de valeurs ou une combinaison de valeurs et d’opérateurs de comparaison.  
  
 **ID d’erreur :** BC40052  
  
### Pour corriger cette erreur  
  
-   Modifiez la plage pour inclure toutes les valeurs, ou utilisez une instruction `Case Else` pour intercepter une valeur non définie.  
  
## Voir aussi  
 [Select...Case Statement](/dotnet/visual-basic/language-reference/statements/select-case-statement)   
 [Decision Structures](/dotnet/visual-basic/programming-guide/language-features/control-flow/decision-structures)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)