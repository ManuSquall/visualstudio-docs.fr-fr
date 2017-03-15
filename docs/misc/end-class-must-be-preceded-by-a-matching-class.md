---
title: "&#39;End Class&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;Class&#39; correspondant | Microsoft Docs"
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
  - "vbc30460"
  - "bc30460"
helpviewer_keywords: 
  - "BC30460"
ms.assetid: 0e6989da-f281-4ac4-8579-b6d627be8de8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Class&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;Class&#39; correspondant
L’instruction `End Class` permet de terminer un bloc `Class` ; elle ne peut donc figurer qu’à la fin du bloc. Soit vous avez une instruction `End Class` redondante, soit votre instruction `End Class` apparaît en dehors des limites de son bloc `Class` correspondant.  
  
 **ID d’erreur :** BC30460  
  
### Pour corriger cette erreur  
  
-   Recherchez et supprimez toutes les instructions `End Class` redondantes.  
  
-   Déplacez l’instruction `End Class` vers l’emplacement approprié dans votre code.  
  
## Voir aussi  
 [End \<keyword\> Statement](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)