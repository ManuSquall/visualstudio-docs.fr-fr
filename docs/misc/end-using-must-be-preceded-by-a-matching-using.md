---
title: "&#39;End Using&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;Using&#39; correspondant | Microsoft Docs"
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
  - "bc36007"
  - "vbc36007"
helpviewer_keywords: 
  - "BC36007"
ms.assetid: 10fb31ba-9b6c-403f-bacc-c7b5df14f1dd
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Using&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;Using&#39; correspondant
Une instruction `End Using` n’est précédée d’aucune déclaration `Using` correspondante.  
  
 **ID d’erreur :** BC36007  
  
### Pour corriger cette erreur  
  
-   Supprimez l’instruction `End Using` si elle est redondante.  
  
-   Fournissez la [Using Statement](/dotnet/visual-basic/language-reference/statements/using-statement) si elle est manquante.  
  
-   Déplacez l’instruction `End Using` à l’emplacement approprié dans le code.  
  
## Voir aussi  
 [End \<keyword\> Statement](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)