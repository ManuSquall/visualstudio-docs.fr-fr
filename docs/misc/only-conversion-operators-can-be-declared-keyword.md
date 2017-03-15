---
title: "Seuls les op&#233;rateurs de conversion peuvent &#234;tre d&#233;clar&#233;s &#39;&lt;mot_cl&#233;&gt;&#39; | Microsoft Docs"
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
  - "bc33019"
  - "vbc33019"
helpviewer_keywords: 
  - "BC33019"
ms.assetid: 946266fe-a909-41b1-aad4-f85dc8050b88
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Seuls les op&#233;rateurs de conversion peuvent &#234;tre d&#233;clar&#233;s &#39;&lt;mot_cl&#233;&gt;&#39;
Un [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement) spécifie [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) ou [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing) alors que l’opérateur n’est pas un opérateur de conversion.  
  
 Chaque opérateur doit être déclaré à la fois [Public](/dotnet/visual-basic/language-reference/modifiers/public) et [Shared](/dotnet/visual-basic/language-reference/modifiers/shared). Toutefois, seul un opérateur de conversion peut être déclaré [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) ou [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing), mais pas les deux en même temps.  
  
 Une définition d’opérateur peut éventuellement inclure les mots clés [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads) et [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows). Aucun autre mot clé n’est autorisé dans un [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement).  
  
 **ID d’erreur :** BC33019  
  
### Pour corriger cette erreur  
  
1.  Supprimez le mot clé `Widening` ou `Narrowing` de la définition de l’opérateur. Ces mots clés ne s’appliquent pas, car aucune conversion de type n’a lieu.  
  
## Voir aussi  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Type Conversions in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)