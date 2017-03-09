---
title: "&#39;Sub New&#39; ne peut pas g&#233;rer d’&#233;v&#233;nements | Microsoft Docs"
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
  - "vbc30497"
  - "bc30497"
helpviewer_keywords: 
  - "BC30497"
ms.assetid: b8a546c4-914e-49de-b553-9fc0f41424ed
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Sub New&#39; ne peut pas g&#233;rer d’&#233;v&#233;nements
Vous avez tenté d’associer `Sub New` avec `Handles`, ce qui n’est pas valide. Utilisez le mot clé `Handles` à la fin d'une déclaration de procédure pour que celle\-ci gère les événements déclenchés par une variable objet déclarée à l'aide du mot clé `WithEvents`.  
  
 **ID d’erreur :** BC30497  
  
### Pour corriger cette erreur  
  
1.  n’utilisez pas `New` dans ce contexte.  
  
## Voir aussi  
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)   
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [WithEvents](/dotnet/visual-basic/language-reference/modifiers/withevents)