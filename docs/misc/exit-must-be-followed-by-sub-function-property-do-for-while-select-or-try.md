---
title: "&#39;Exit&#39; doit &#234;tre suivi de &#39;Sub&#39;, &#39;Function&#39;, &#39;Property&#39;, &#39;Do&#39;, &#39;For&#39;, &#39;While&#39;, &#39;Select&#39; ou &#39;Try&#39; | Microsoft Docs"
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
  - "bc30240"
  - "vbc30240"
helpviewer_keywords: 
  - "BC30240"
ms.assetid: 91078689-f4bf-4331-a475-10bc9fe7cd0c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit&#39; doit &#234;tre suivi de &#39;Sub&#39;, &#39;Function&#39;, &#39;Property&#39;, &#39;Do&#39;, &#39;For&#39;, &#39;While&#39;, &#39;Select&#39; ou &#39;Try&#39;
Une instruction `Exit` contient un mot clé non valide.`Exit` doit spécifier le bloc à partir duquel le contrôle doit être transféré à l’instruction qui suit le bloc. Par exemple : `End While`.  
  
 **ID d’erreur :** BC30240  
  
### Pour corriger cette erreur  
  
-   Ajoutez un mot clé valide après `Exit` ou supprimez l’instruction `Exit`.  
  
## Voir aussi  
 [Exit Statement](/dotnet/visual-basic/language-reference/statements/exit-statement)