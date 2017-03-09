---
title: "Le constructeur doit &#234;tre d&#233;clar&#233; en tant que Sub, et non Function. | Microsoft Docs"
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
  - "bc30493"
  - "vbc30493"
helpviewer_keywords: 
  - "BC30493"
ms.assetid: bcacfd4b-cac0-4ad3-a6df-5fb37c189e8f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le constructeur doit &#234;tre d&#233;clar&#233; en tant que Sub, et non Function.
Vous avez tenté de déclarer un `Function New`. Les constructeurs doivent être déclarés en tant que `Sub New`.  
  
 **ID d’erreur :** BC30493  
  
### Pour corriger cette erreur  
  
-   Utilisez `Sub` à la place de `Function`.  
  
## Voir aussi  
 [Sub Statement](/dotnet/visual-basic/language-reference/statements/sub-statement)