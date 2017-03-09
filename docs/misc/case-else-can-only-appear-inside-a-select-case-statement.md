---
title: "&#39;Case Else&#39; ne peut appara&#238;tre qu’&#224; l’int&#233;rieur d’une instruction &#39;Select Case&#39; | Microsoft Docs"
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
  - "bc30071"
  - "vbc30071"
helpviewer_keywords: 
  - "BC30071"
ms.assetid: 9a4f8ccb-717a-4d18-91b4-4a373202c38a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Case Else&#39; ne peut appara&#238;tre qu’&#224; l’int&#233;rieur d’une instruction &#39;Select Case&#39;
Une instruction `Case Else` se trouve en dehors d’un bloc `Select`. Une instruction `Case Else` peut être utilisée uniquement entre une instruction `Select` ou `Select Case` et son instruction `End Select` correspondante.  
  
 **ID d’erreur :** BC30071  
  
### Pour corriger cette erreur  
  
-   Supprimez l’instruction `Case Else` ou déplacez\-la vers un bloc `Select`.  
  
## Voir aussi  
 [Select...Case Statement](/dotnet/visual-basic/language-reference/statements/select-case-statement)