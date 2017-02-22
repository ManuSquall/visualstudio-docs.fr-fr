---
title: "Contr&#244;le de la collecte de donn&#233;es dans les outils de profilage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tâches avancées (outils de profilage)"
  - "outils de profilage, tâches avancées"
ms.assetid: e713ad63-b948-46f3-8db9-59b30922ebe5
caps.latest.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 27
---
# Contr&#244;le de la collecte de donn&#233;es dans les outils de profilage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Grâce aux outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous pouvez contrôler le moment où les données de profilage sont collectées lors d'une session de performance et spécifier les fonctions profilées.  Cette section explique comment démarrer et arrêter la collecte de données à partir des fenêtres **Explorateur de performances** et **Contrôle de collecte de données**, et comment limiter les objets pour lesquels les données de profilage sont recueillies.  
  
## Tâches courantes  
  
|Tâche|Contenu associé|  
|-----------|---------------------|  
|**Démarrer et arrêter le profilage :** vous pouvez commencer à profiler une application au démarrage de cette dernière, ou vous pouvez joindre le profileur à un processus qui s'exécute déjà.  Lorsque l'application cible est en cours d'exécution, vous pouvez suspendre et reprendre la collecte de données.  Pour arrêter une session de profilage, fermez l'application cible ou détachez le profileur d'un processus en cours d'exécution.|-   [Procédure : démarrer et arrêter le profilage](../profiling/how-to-start-and-end-performance-data-collection.md)<br />-   [Procédure : attacher le profileur à des processus en cours d’exécution ou l’en détacher](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)<br />-   [Comment : suspendre et reprendre le profilage](../Topic/How%20to:%20Pause%20and%20Resume%20Performance%20Data%20Collection.md)|  
|**Configurer le profilage par instrumentation afin de limiter les données collectées :** vous pouvez utiliser les propriétés de configuration de session de performance pour limiter les données collectées dans les exécutions de profilage qui utilisent la méthode d'instrumentation.  Vous pouvez inclure ou exclure des fichiers .dll, des espaces de noms, des classes et des fonctions spécifiques.  Vous pouvez également exclure des fonctions qui ne respectent pas un seuil de taille que vous spécifiez.|-   [Procédure : limiter l’instrumentation à des DLL spécifiques](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)<br />-   [Comment : limiter l’instrumentation à des fonctions spécifiques](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [Procédure : exclure ou inclure les fonctions courtes de l’instrumentation](../Topic/How%20to:%20Exclude%20or%20Include%20Short%20Functions%20from%20Instrumentation.md)|  
  
## Rubriques connexes  
 [Configuration de sessions de performance](../profiling/configuring-performance-sessions.md)  
  
## Voir aussi  
 [Utilisation des outils de profilage](../profiling/performance-explorer.md)