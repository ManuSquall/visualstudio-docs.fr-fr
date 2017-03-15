---
title: "Profilage de services &#224; partir de la ligne de commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "outils de profilage, services"
  - "profiler des services"
ms.assetid: f0d62318-b0e8-49c6-9a30-9f7a6adef2f6
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Profilage de services &#224; partir de la ligne de commande
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette section décrit les procédures et les options de collecte des données de performance pour les services Windows à l'aide des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] à partir de la ligne de commande.  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée dans windows 8 et Windows Server 2012 requises des modifications significatives de la manière que le profileur Visual Studio collecte des données sur ces plateformes.  Les applications de mémoire de fenêtres requièrent également de nouvelles techniques de collection.  Consultez [Profilage d'applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## Tâches courantes  
  
|Tâche|Contenu associé|  
|-----------|---------------------|  
|**Collecter des statistiques de l'application :** utilisez la méthode d'échantillonnage pour collecter des statistiques de performance.  Les données d'échantillonnage sont utiles pour analyser les problèmes d'utilisation de l'UC et pour comprendre les caractéristiques de performance générales d'une application.|-   [Collecte de statistiques d'applications en utilisant l'échantillonnage](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
|**Collecter des données de minutage détaillées :** utilisez la méthode d'instrumentation pour collecter des informations de minutage détaillées.  Les données d'instrumentation sont utiles pour analyser les problèmes d'E\/S et pour l'analyse affinée des scénarios d'application.|-   [Collecte de données de temporisation détaillées à l'aide de l'instrumentation](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
|**Collecter des données de la mémoire .NET :** utilisez l'échantillonnage ou l'instrumentation pour collecter des données d'allocation de mémoire .NET qui indiquent la taille et le nombre d'objets alloués.  Vous pouvez également collecter des données de durée de vie d'objet qui indiquent la taille et le nombre d'objets qui sont récupérés dans chaque génération de garbage collection.|-   [Collecte de données de mémoire .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
|**Collecter des données de concurrence :** utilisez la méthode de concurrence pour collecter des données de conflit de ressources et des données d'activité de thread qui indiquent l'utilisation de l'UC, les conflits de threads, la migration de threads, les retards de synchronisation, les zones d'E\/S superposées et d'autres événements système.|-   [Collecte de données de concurrence](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
|**Ajouter des données sur l'interaction entre les couches :** vous pouvez ajouter des données de performances sur les appels ADO.NET synchrones que le service a passés à une base de données Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)].|-   [Collecte de données d’interaction de couche](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## Tâches connexes  
  
|Tâche|Contenu associé|  
|-----------|---------------------|  
|**Profiler les applications autonomes \(clientes\)**|-   [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**Profiler des applications ASP.NET**|-   [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)|