---
title: "Collecte de donn&#233;es de concurrence pour un service en utilisant la ligne de commande du profileur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 275aacba-b2af-4d34-8931-ee30d777a256
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Collecte de donn&#233;es de concurrence pour un service en utilisant la ligne de commande du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La méthode de concurrence des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vous permet de collecter des données de conflit de ressources et des données d'activité de thread qui indiquent l'utilisation de l'UC, les conflits de threads, la migration de threads, les retards de synchronisation, les zones d'E\/S superposées et d'autres événements système.  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée dans windows 8 et Windows Server 2012 requises des modifications significatives de la manière que le profileur Visual Studio collecte des données sur ces plateformes.  Les applications de mémoire de fenêtres requièrent également de nouvelles techniques de collection.  Consultez [Profilage d'applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## Tâches courantes  
  
|Tâche|Contenu associé|  
|-----------|---------------------|  
|**Attacher à un service .NET en cours d'exécution**|-   [Comment : attacher le profileur à un service .NET pour collecter des données de concurrence](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Ajouter des données sur l'interaction entre les couches**|-   [Collecte de données d’interaction de couche](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**Attacher à un service C\/C\+\+ en cours d'exécution**|-   [Comment : attacher le profileur à un service natif pour collecter des données de concurrence](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
## Tâches connexes  
  
### Profilage des services Windows  
  
|Tâche|Contenu associé|  
|-----------|---------------------|  
|**Profiler à l'aide de la méthode d'échantillonnage**|-   [Collecte de statistiques d'applications en utilisant l'échantillonnage](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
|**Profiler à l'aide de la méthode d'instrumentation**|-   [Collecte de données de temporisation détaillées à l'aide de l'instrumentation](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
|**Profiler l'allocation de mémoire et le garbage collection .NET**|-   [Collecte de données de mémoire .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
  
### Profilage de données d'accès concurrentiel  
  
|Tâche|Contenu associé|  
|-----------|---------------------|  
|**Profiler des applications autonomes**|-   [Collecte de données concurrentielles](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Profiler des applications Web ASP.NET**|-   [Collecte de données concurrentielles](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### Analyse des vues de données et des rapports de concurrence  
 [Vues de données de conflit de ressources](../profiling/resource-contention-data-views.md)  
  
 [Visualiseur concurrence](../profiling/concurrency-visualizer.md)  
  
## Référence  
 [Référence d'outils de profilage de ligne de commande](../profiling/command-line-profiling-tools-reference.md)