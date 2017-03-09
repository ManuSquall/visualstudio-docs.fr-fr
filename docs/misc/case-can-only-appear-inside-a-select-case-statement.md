---
title: "&#39;Case&#39; ne peut appara&#238;tre qu’&#224; l’int&#233;rieur d’une instruction &#39;Select Case&#39; | Microsoft Docs"
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
  - "vbc30072"
  - "bc30072"
helpviewer_keywords: 
  - "BC30072"
ms.assetid: da808bc3-f154-444a-b547-3cf55beff8a9
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Case&#39; ne peut appara&#238;tre qu’&#224; l’int&#233;rieur d’une instruction &#39;Select Case&#39;
Une instruction `Case` se trouve en dehors d’un bloc `Select`. Une instruction `Case` peut être utilisée uniquement entre une instruction `Select` ou `Select Case` et son instruction `End Select` correspondante.  
  
 **ID d’erreur :** BC30072  
  
### Pour corriger cette erreur  
  
-   Supprimez l’instruction `Case` ou déplacez\-la dans un bloc `Select`.  
  
## Voir aussi  
 [Select...Case Statement](/dotnet/visual-basic/language-reference/statements/select-case-statement)