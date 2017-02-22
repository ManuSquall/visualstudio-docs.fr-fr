---
title: "Collecte de statistiques d&#39;applications pour les services en utilisant la m&#233;thode d&#39;&#233;chantillonnage du profileur | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 07840ab2-3a92-4744-ac87-48b19e0ceecd
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Collecte de statistiques d&#39;applications pour les services en utilisant la m&#233;thode d&#39;&#233;chantillonnage du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette section décrit les procédures et options pour collecter des statistiques de performance pour les services Windows à l'aide de la méthode d'échantillonnage à partir de la ligne de commande.  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée dans windows 8 et Windows Server 2012 requises des modifications significatives de la manière que le profileur Visual Studio collecte des données sur ces plateformes.  Les applications de mémoire de fenêtres requièrent également de nouvelles techniques de collection.  Consultez [Profilage d'applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## Tâches courantes  
  
|Tâche|Contenu associé|  
|-----------|---------------------|  
|**Attacher le profileur à un service .NET**|-   [Comment : attacher le profileur à un service .NET pour collecter des statistiques d'applications](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)|  
|**Ajouter des données sur l'interaction entre les couches**|-   [Collecte de données d’interaction de couche](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**Attacher le profileur à un service C\/C\+\+**|-   [Comment : attacher le profileur à un service natif pour collecter des statistiques d'applications](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|  
  
## Tâches connexes  
  
### Profilage des services Windows  
  
|Tâche|Contenu associé|  
|-----------|---------------------|  
|**Profiler à l'aide de la méthode d'instrumentation**|-   [Collecte de données de temporisation détaillées à l'aide de l'instrumentation](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
|**Profiler l'allocation de mémoire et le garbage collection .NET**|-   [Collecte de données de mémoire .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
|**Profiler le conflit de ressources et l'activité du thread**|-   [Collecte de données de concurrence](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
  
### Profilage à l'aide de la méthode d'échantillonnage  
  
|Tâche|Contenu associé|  
|-----------|---------------------|  
|**Profiler les applications autonomes \(clientes\)**|-   [Collecte de statistiques d’applications en utilisant l’échantillonnage](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Profiler des applications Web ASP.NET**|-   [Collecte de statistiques d’applications en utilisant l’échantillonnage](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
  
### Analyse des vues de données et des rapports d'échantillonnage  
 [Vues de données de la méthode d'échantillonnage](../profiling/profiler-sampling-method-data-views.md)