---
title: "L’op&#233;rateur &#39;&lt;op&#233;rateur&gt;&#39; doit avoir deux param&#232;tres | Microsoft Docs"
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
  - "bc33015"
  - "vbc33015"
helpviewer_keywords: 
  - "BC33015"
ms.assetid: 506ea996-8abe-4dbe-aff4-d3910bf4399e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’op&#233;rateur &#39;&lt;op&#233;rateur&gt;&#39; doit avoir deux param&#232;tres
Un opérateur binaire est défini avec moins de deux ou plus de deux paramètres.  
  
 Un opérateur binaire doit avoir exactement deux paramètres.  
  
 **ID d’erreur :** BC33015  
  
### Pour corriger cette erreur  
  
-   Modifiez la définition de façon à spécifier exactement deux paramètres.  
  
-   Si vous n’avez besoin que d’un seul paramètre, vous devez définir un opérateur unaire.  
  
-   Si vous n’avez besoin d’aucun paramètre ou si vous en avez besoin de plus de deux, vous devez utiliser [Function Statement](/dotnet/visual-basic/language-reference/statements/function-statement) pour définir une procédure `Function` au lieu d’un opérateur.  
  
## Voir aussi  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)