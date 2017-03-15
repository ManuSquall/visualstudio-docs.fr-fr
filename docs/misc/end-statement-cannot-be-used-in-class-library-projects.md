---
title: "L’instruction &#39;End&#39; ne peut pas &#234;tre utilis&#233;e dans les projets de biblioth&#232;que de classes | Microsoft Docs"
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
  - "bc30615"
  - "vbc30615"
helpviewer_keywords: 
  - "BC30615"
ms.assetid: c8606b17-b50b-4014-b76e-b748d57e9389
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’instruction &#39;End&#39; ne peut pas &#234;tre utilis&#233;e dans les projets de biblioth&#232;que de classes
Les projets de bibliothèque de classes utilisés pour créer des DLL n’autorisent pas l’utilisation du mot clé `End` pour arrêter l’exécution du code dans une procédure.  
  
 **ID d’erreur :** BC30615  
  
### Pour corriger cette erreur  
  
-   Utilisez des structures de contrôle telles que `While` et `For` pour contrôler le flux d’exécution du programme.  
  
## Voir aussi  
 [Control Flow](/dotnet/visual-basic/programming-guide/language-features/control-flow/index)