---
title: "Arr&#234;t du d&#233;bogage en cours, bo&#238;te de dialogue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.stopnow"
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
  - "Arrêt du débogage en cours (boîte de dialogue)"
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Arr&#234;t du d&#233;bogage en cours, bo&#238;te de dialogue
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette boîte de dialogue s'affiche lorsque le débogueur tente d'arrêter une session de débogage, mais que l'arrêt de la session prend du temps.  L'arrêt d'une session de débogage est généralement très rapide et cette boîte de dialogue ne s'affiche pas.  Cependant, il arrive que l'opération prenne du temps pour détacher tous les processus débogués.  Si l'arrêt de la session dépasse quelques secondes \(ou si une erreur de détachement se produit\), cette boîte de dialogue apparaît.  Si cela se produit fréquemment, cela peut être dû à un problème interne et vous pouvez contacter le Support Technique Microsoft.  
  
 Vous pouvez attendre le détachement des processus et la disparition de cette boîte de dialogue, ou utiliser le bouton **Arrêter maintenant** pour forcer l'arrêt immédiat.  
  
 **Arrêter maintenant**  
 Cliquez sur le bouton pour terminer immédiatement la session de débogage.  L'utilisation du bouton **Arrêter maintenant** permet de mettre fin aux processus en cours de débogage plutôt que de les détacher.  Si vous déboguez des processus système, l'arrêt de ces processus avec **Arrêter maintenant** peut entraîner des effets inattendus et indésirables.  
  
## Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Detaching Programs](http://msdn.microsoft.com/fr-fr/f2c756c2-8079-474b-94c2-01c19a141a01)