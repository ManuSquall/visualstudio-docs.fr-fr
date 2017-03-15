---
title: "&#39;Loop&#39; ne peut pas avoir de condition si le &#39;Do&#39; correspondant en a une | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30238"
  - "bc30238"
helpviewer_keywords: 
  - "BC30238"
ms.assetid: 81513cb5-69e7-4d62-b33e-e54cb8c5e8bf
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Loop&#39; ne peut pas avoir de condition si le &#39;Do&#39; correspondant en a une
Une instruction `Loop` contient une clause `While` ou `Until`, et l’instruction `Do` correspondante contient également une telle clause. Une condition peut être spécifiée soit par l’instruction `Do`, soit par l’instruction `Loop` d’une boucle, et non par les deux.  
  
 **ID d’erreur :** BC30238  
  
### Pour corriger cette erreur  
  
-   Supprimez la clause `While` ou `Until` de l’instruction `Do` ou de l’instruction `Loop`.  
  
## Voir aussi  
 [Do...Loop Statement](/dotnet/visual-basic/language-reference/statements/do-loop-statement)