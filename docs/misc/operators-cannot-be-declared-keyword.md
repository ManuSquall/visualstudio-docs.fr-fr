---
title: "Les op&#233;rateurs ne peuvent pas &#234;tre d&#233;clar&#233;s &#39;&lt;mot_cl&#233;&gt;&#39; | Microsoft Docs"
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
  - "vbc33013"
  - "bc33013"
helpviewer_keywords: 
  - "BC33013"
ms.assetid: bfd805f4-e30e-4553-9cb7-2690595f0480
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les op&#233;rateurs ne peuvent pas &#234;tre d&#233;clar&#233;s &#39;&lt;mot_cl&#233;&gt;&#39;
Un opérateur est déclaré avec un mot clé qui n’est pas valide dans le cadre des définitions d’opérateur.  
  
 Chaque opérateur doit être déclaré à la fois [Public](/dotnet/visual-basic/language-reference/modifiers/public) et [Shared](/dotnet/visual-basic/language-reference/modifiers/shared). En outre, un opérateur de conversion doit être déclaré avec [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) ou [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing), mais pas les deux. Une définition d’opérateur peut éventuellement inclure le mot clé [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads) ou [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows). Aucun autre mot clé n’est autorisé dans un [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement).  
  
 **ID d’erreur :** BC33013  
  
### Pour corriger cette erreur  
  
-   Supprimez le mot clé non valide de la définition de l’opérateur.  
  
## Voir aussi  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)