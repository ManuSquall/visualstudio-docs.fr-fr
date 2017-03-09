---
title: "Cette instruction ne peut pas appara&#238;tre dans le corps d’un &#233;v&#233;nement | Microsoft Docs"
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
  - "bc31112"
  - "vbc31112"
helpviewer_keywords: 
  - "BC31112"
ms.assetid: fd51fc53-a008-4b79-85fb-2d9fa1fb5a79
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Cette instruction ne peut pas appara&#238;tre dans le corps d’un &#233;v&#233;nement
Cette instruction ne peut pas apparaître dans le corps d’un événement. Elle est interprétée comme la fin de l’événement.  
  
 Une instruction apparaît dans le corps d’un événement alors qu’elle n’est pas valide dans celui\-ci.  
  
 **ID d’erreur :** BC31112  
  
### Pour corriger cette erreur  
  
-   Ajoutez un `End Event` avant l’instruction.  
  
## Voir aussi  
 [Application Events Sample](http://msdn.microsoft.com/fr-fr/289a787f-b97e-43c8-a304-fe95e45f4a0d)   
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)