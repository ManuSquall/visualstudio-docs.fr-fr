---
title: "Code mixte et informations manquantes dans la fen&#234;tre Pile des appels | Microsoft Docs"
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
  - "SQL"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "code managé, exécution pas à pas"
  - "Pile des appels (fenêtre), débogage en mode mixte"
  - "Pile des appels (fenêtre), résolution des problèmes"
  - "frames natifs"
  - "piles des appels managées"
  - "débogage en mode mixte, pile des appels"
  - "exécution pas à pas, code managé"
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Code mixte et informations manquantes dans la fen&#234;tre Pile des appels
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En raison de différences entre la pile des appels du code managé et celle du code natif, le débogueur ne peut pas toujours afficher la pile des appels complète en cas de types de code mixtes.  Lorsque du code natif appelle du code managé, vous pouvez noter les divergences suivantes dans la fenêtre **Pile des appels** :  
  
-   Le frame natif situé immédiatement au\-dessus du code managé peut ne pas apparaître dans la fenêtre **Pile des appels**.  Pour plus d'informations, consultez [Comment : effectuer un pas à pas sortant du code managé lorsque les frames natifs sont absents de la fenêtre Pile des appels](../Topic/How%20to:%20Step%20out%20of%20Managed%20Code%20when%20Native%20Frames%20are%20Missing%20from%20the%20Call%20Stack%20Window.md).  
  
-   Pour les applications en mode mixte lancées en dehors du débogueur, la fenêtre **Pile des appels** peut n'afficher que le code managé et aucun des frames natifs ne sera visible.  
  
 Ces deux situations sont assez rares.  Dans la plupart des appels natifs au code managé, les piles d'appels apparaissent correctement.  
  
## Voir aussi  
 [Comment : utiliser la fenêtre Pile des appels](../debugger/how-to-use-the-call-stack-window.md)