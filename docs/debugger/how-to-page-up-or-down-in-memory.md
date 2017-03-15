---
title: "Comment&#160;: se d&#233;placer d&#39;une page vers le haut ou vers le bas dans la m&#233;moire | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "débogueur, déplacement d’une page vers le haut ou vers le bas dans la mémoire"
  - "mémoire, déplacement d’une page vers le haut ou vers le bas"
  - "Code Machine (fenêtre), affichage de l’espace mémoire"
  - "Mémoire (fenêtre), déplacement d’une page vers le haut ou vers le bas dans la mémoire"
ms.assetid: 50b30a68-66f6-43f8-a48b-59ce12c95471
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Comment&#160;: se d&#233;placer d&#39;une page vers le haut ou vers le bas dans la m&#233;moire
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lorsque vous affichez le contenu de la mémoire dans la fenêtre **Mémoire** ou **Code Machine**, vous pouvez vous servir de la barre de défilement verticale pour vous déplacer dans l'espace mémoire.  
  
### Pour vous déplacer d'une page vers le haut ou vers le bas dans la mémoire  
  
1.  Pour vous déplacer d'une page vers le bas \(atteindre une adresse mémoire supérieure\), cliquez dans la barre de défilement verticale au\-dessous de la case de défilement.  
  
2.  Pour vous déplacer d'une page vers le haut \(atteindre une adresse mémoire inférieure\), cliquez dans la barre de défilement verticale au\-dessus du curseur.  
  
 Remarquez que la barre de défilement verticale ne se comporte pas de manière habituelle.  L'espace adresse d'un ordinateur moderne est très importante, et il serait facile de se perdre en faisant glisser le curseur de défilement vers un emplacement aléatoire.  Pour cette raison, le curseur est « fixé » et reste toujours au milieu de la barre de défilement.  Dans les applications en code natif, vous pouvez vous déplacer d'une page vers le haut ou vers le bas, mais il est impossible de défiler librement.  
  
 Dans les applications managées, le désassemblage se limitant à une fonction, vous pouvez utiliser le défilement normal.  
  
 Remarquez que l'adresse la plus haute est affichée en bas de la fenêtre.  Pour afficher une adresse plus haute, vous devez descendre et non pas monter.  
  
#### Pour monter ou descendre d'une instruction  
  
-   Cliquez sur la flèche en haut ou en bas de la barre de défilement vertical.  
  
## Voir aussi  
 [Fenêtres Mémoire](../debugger/memory-windows.md)   
 [Comment : utiliser la fenêtre Code Machine](../debugger/how-to-use-the-disassembly-window.md)   
 [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)