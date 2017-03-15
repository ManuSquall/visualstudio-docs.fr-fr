---
title: "Temps de traitement UI | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.uiprocessing"
helpviewer_keywords: 
  - "Visualiseur concurrence, Temps de traitement UI"
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Temps de traitement UI
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ces segments de la chronologie sont associés aux temps de blocage catégorisés comme traitement de l'interface utilisateur.  Cela implique qu'un thread consomme des messages Windows ou effectue un autre travail lié à l'interface utilisateur.  Pendant ce temps, un thread a été bloqué dans une API que le visualiseur d'accès concurrentiel considère comme traitement de l'interface utilisateur.  Les API telles que `GetMessage()` et `MsgWaitForMultipleObjects()` appartiennent à ce groupe.  
  
 Si aucune API de blocage prédéfinie n'est identifiée, examinez les piles d'appels et les rapports de profil pour déterminer les causes sous\-jacentes du délai.  
  
 La catégorie Traitement de l'interface utilisateur est importante dans le fonctionnement de la réactivité des applications d'interface GUI et est souhaitable dans les applications qui dépendent de la réactivité d'une interface utilisateur.  Par exemple, si le thread UI d'une application passe 100 % de son temps dans la catégorie Traitement de l'interface utilisateur, cela indique qu'il est probablement très réactif.  Toutefois, si le thread UI passe un temps considérable dans d'autres catégories, déterminez les causes premières et envisagez des options pour la réduction de catégories non liées à l'interface utilisateur sur ce thread.  
  
## Voir aussi  
 [vue Threads](../profiling/threads-view-parallel-performance.md)