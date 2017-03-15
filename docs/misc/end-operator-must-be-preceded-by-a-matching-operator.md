---
title: "&#39;End Operator&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;Operator&#39; correspondant | Microsoft Docs"
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
  - "vbc33007"
  - "bc33007"
helpviewer_keywords: 
  - "BC33007"
ms.assetid: 57df3e01-0858-4cf7-9295-075a2c0c4bde
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Operator&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;Operator&#39; correspondant
Une instruction `End Operator` n’est précédée d’aucune déclaration `Operator` correspondante.  
  
 **ID d’erreur :** BC33007  
  
### Pour corriger cette erreur  
  
-   Supprimez l’instruction `End Operator` si elle est redondante.  
  
-   Fournissez la procédure `Operator` manquante, le cas échéant.  
  
-   Déplacez l’instruction `End Operator` à l’emplacement approprié dans le code.  
  
## Voir aussi  
 [End \<keyword\> Statement](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)   
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)