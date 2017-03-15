---
title: "Profilage d’applications autonomes &#224; partir de la ligne de commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "outils de profilage, applications autonomes"
  - "profilage d’applications autonomes"
ms.assetid: a47f2bf2-186d-4120-bb79-34e2f3a1ee42
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Profilage d’applications autonomes &#224; partir de la ligne de commande
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette section décrit les procédures et options de collecte de données de performances pour les applications \(clientes\) autonomes à l'aide des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] à partir de la ligne de commande.  
  
## Tâches courantes  
  
|Tâche|Contenu associé|  
|-----------|---------------------|  
|**Collecter des statistiques de l'application :** utilisez la méthode d'échantillonnage pour collecter des statistiques de performance.  Les données d'échantillonnage sont utiles pour analyser les problèmes d'utilisation de l'UC et pour comprendre les caractéristiques de performance générales d'une application.|-   [Collecte de statistiques d’applications en utilisant l’échantillonnage](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Collecter des données de minutage détaillées :** utilisez la méthode d'instrumentation pour collecter des informations de minutage détaillées.  Les données d'instrumentation sont utiles pour analyser les problèmes d'E\/S et pour l'analyse affinée des scénarios d'application.|-   [Collecte de données de temporisation détaillées à l’aide de l’instrumentation](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Collecter des données de la mémoire .NET :** utilisez l'échantillonnage ou l'instrumentation pour collecter des données d'allocation de mémoire .NET qui indiquent la taille et le nombre d'objets alloués.  Vous pouvez également collecter des données de durée de vie d'objet qui indiquent la taille et le nombre d'objets qui sont récupérés dans chaque génération de garbage collection.|-   [Collecte de données de mémoire .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Collecter des données de concurrence :** utilisez la méthode de concurrence pour collecter des données de conflit de ressources et des données d'activité de thread qui indiquent l'utilisation de l'UC, les conflits de threads, la migration de threads, les retards de synchronisation, les zones d'E\/S superposées et d'autres événements système.|-   [Collecte de données concurrentielles](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Ajouter des données sur l'interaction entre les couches :** vous pouvez ajouter des données de performances sur les appels ADO.NET synchrones que l'application a passés à une base de données Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)].  Ajout de données sur l'interaction entre les couches à une exécution du profilage requiert des procédures spécifiques avec les outils de profilage de ligne de commande.|-   [Collecte de données d’interaction de couche](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**Essayer par soi\-même :** utilisez des procédures pas à pas pour profiler un exemple d'application cliente à l'aide de la méthode d'échantillonnage ou d'instrumentation.|-   [Procédure pas à pas : profilage de la ligne de commande à l’aide de l’échantillonnage](../Topic/Walkthrough:%20Command-Line%20Profiling%20Using%20Sampling.md)<br />-   [Procédure pas à pas : profilage de la ligne de commande à l’aide de l’instrumentation](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)|  
  
## Tâches connexes  
  
|Tâche|Contenu associé|  
|-----------|---------------------|  
|**Profiler des applications ASP.NET**|-   [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)|  
|**Profiler des services**|-   [Profilage de services](../profiling/command-line-profiling-of-services.md)|