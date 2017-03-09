---
title: "&#39;Continue&#160;Do&#39; ne peut figurer qu’&#224; l’int&#233;rieur d’une instruction &#39;Do&#39;. | Microsoft Docs"
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
  - "vbc30782"
  - "bc30782"
helpviewer_keywords: 
  - "BC30782"
ms.assetid: c6b35e63-4d84-449d-9685-41a1bc0a7f35
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Continue&#160;Do&#39; ne peut figurer qu’&#224; l’int&#233;rieur d’une instruction &#39;Do&#39;.
Une instruction `Continue Do` ne peut figurer qu’à l’intérieur d’une boucle `Do...Loop`.  
  
 **ID d’erreur :** BC30782  
  
### Pour corriger cette erreur  
  
1.  Si l’instruction `Continue Do` se trouve dans une boucle `For...Next`, remplacez l’instruction par `Continue For`.  
  
2.  Si l’instruction `Continue Do` se trouve dans une boucle `While...End While`, remplacez l’instruction par `Continue While`.  
  
3.  Sinon, supprimez l’instruction `Continue Do`.  
  
## Voir aussi  
 [Continue Statement](/dotnet/visual-basic/language-reference/statements/continue-statement)   
 [Do...Loop Statement](/dotnet/visual-basic/language-reference/statements/do-loop-statement)