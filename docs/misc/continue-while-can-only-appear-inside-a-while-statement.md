---
title: "&#39;Continue While&#39; ne peut appara&#238;tre que dans une instruction &#39;While&#39; | Microsoft Docs"
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
  - "vbc30784"
  - "bc30784"
helpviewer_keywords: 
  - "BC30784"
ms.assetid: b26c77b2-36ae-4dce-b048-f7c4b196faa4
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Continue While&#39; ne peut appara&#238;tre que dans une instruction &#39;While&#39;
Une instruction `Continue While` ne peut figurer qu’à l’intérieur d’une boucle `For...Next`.  
  
 **ID d’erreur :** BC30784  
  
### Pour corriger cette erreur  
  
1.  Si l’instruction `Continue While` figure dans une boucle `Do...Loop`, remplacez l’instruction par `Continue Do`.  
  
2.  Si l’instruction `Continue While` figure dans une boucle `For...Next`, remplacez l’instruction par `Continue For`.  
  
3.  Sinon, supprimez l’instruction `Continue While`.  
  
## Voir aussi  
 [Continue Statement](/dotnet/visual-basic/language-reference/statements/continue-statement)   
 [While...End While Statement](/dotnet/visual-basic/language-reference/statements/while-end-while-statement)