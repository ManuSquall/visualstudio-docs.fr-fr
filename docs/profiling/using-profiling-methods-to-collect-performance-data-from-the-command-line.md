---
title: "Utilisation de m&#233;thodes de profilage pour collecter des donn&#233;es de performance &#224; partir de la ligne de commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Utilisation de m&#233;thodes de profilage pour collecter des donn&#233;es de performance &#224; partir de la ligne de commande
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Votre choix d'options et d'outils en ligne de commande des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dépend de facteurs tels que le type d'application que vous profilez, la méthode de profilage que vous voulez utiliser et si l'application cible est écrite dans le code natif ou [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Cette rubrique organise les rubriques de procédures en ligne de commande d'après la méthode de profilage que vous choisissez.  
  
## Dans cette rubrique  
 [À l'aide de la méthode d'échantillonnage pour collecter des statistiques de performance](#BKMK_Using_the_sampling_method_to_collect_performance_statistics)  
  
 [À l'aide de la méthode d'instrumentation pour collecter des données de temporisation détaillées](#BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data)  
  
 [Utilisation des méthodes de mémoire. NET collecter des données d'allocation de mémoire et de durée de vie de l'objet](#BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data)  
  
 [À l'aide de la méthode de concurrence pour collecter des données de conflit de ressources et de migration des données d'activité](#BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data)  
  
 [Ajout de données sur l'interaction entre les couches à une exécution du profilage](#BKMK_Adding_tier_interaction_data_to_a_profiling_run)  
  
##  <a name="BKMK_Using_the_sampling_method_to_collect_performance_statistics"></a> À l'aide de la méthode d'échantillonnage pour collecter des statistiques de performance  
 La méthode d'échantillonnage des outils de profilage collecte les données de performances à des intervalles spécifiés dans une exécution du profilage.  L'échantillonnage de données peut fournir des informations importantes sur des problèmes de performance liés à l'UC, et c'est certainement un bon moyen de commencer à explorer la performance d'une application.  
  
 Vous pouvez démarrer simultanément le profileur et l'application, ou vous pouvez attacher le profileur à une instance en cours d'exécution d'une application.  
  
|Tâche|Type d'application cible|  
|-----------|------------------------------|  
|**Lancer une application**|-   [Applications autonomes](../profiling/how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Attacher à un processus en cours d'exécution**|-   [Applications autonomes .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)<br />-   [Applications autonomes natives](../Topic/How%20to:%20Attach%20the%20Profiler%20to%20a%20Native%20Stand-Alone%20Application%20and%20Collect%20Application%20Statistics%20by%20Using%20the%20Command%20Line.md)<br />-   [Applications Web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Services .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Services natifs](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|  
  
##  <a name="BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data"></a> À l'aide de la méthode d'instrumentation pour collecter des données de temporisation détaillées  
 La méthode d'instrumentation des outils de profilage collecte les données de performances à partir de copies de fichiers binaires d'application qui contiennent des sondes logicielles pour enregistrer les informations de performance.  Les données d'instrumentation sont collectées au démarrage et à la fin de chaque fonction instrumentée et à chaque appel à d'autres fonctions de la fonction instrumentée.  La méthode d'instrumentation est utile pour découvrir des problèmes de performance avec des problèmes d'E\/S tels que l'utilisation du disque.  
  
 Vous créez le fichier binaire instrumenté avec l'outil [VInstr.exe](../profiling/vsinstr.md).  Après avoir initialisé le profileur, les données sont collectées automatiquement à partir des fichiers binaires instrumentés lorsque vous exécutez l'application cible.  
  
 **Type d'application cible**  
  
-   [Composants autonomes .NET Framework](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
-   [Composants autonomes natifs](../profiling/how-to-instrument-a-native-stand-alone-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
-   [Applications Web ASP.NET statiquement compilées](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)  
  
-   [Applications Web ASP.NET dynamiquement compilées](../Topic/How%20to:%20Instrument%20a%20Dynamically%20Compiled%20ASP.NET%20Web%20Application%20and%20Collect%20Detailed%20Timing%20Data%20with%20the%20Profiler%20by%20Using%20the%20Command%20Line.md)  
  
-   [Services .NET](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
-   [Services natifs](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
##  <a name="BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data"></a> Utilisation des méthodes de mémoire. NET collecter des données d'allocation de mémoire et de durée de vie de l'objet  
 La méthode de la mémoire .NET des outils de profilage vous permet de collecter des données d'allocation de mémoire [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] et des informations sur la durée de vie des objets dans le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Vous pouvez démarrer l'application cible à l'aide du profileur, vous pouvez attacher le profileur à une instance en cours d'exécution d'une application, et vous pouvez créer des versions instrumentées de l'application afin de collecter les informations de minutage détaillées avec les données de la mémoire [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
|Tâche|Type d'application cible|  
|-----------|------------------------------|  
|**Lancer une application**|-   [Applications .NET Framework autonomes](../Topic/How%20to:%20Launch%20a%20Stand-Alone%20.NET%20Framework%20Application%20with%20the%20Profiler%20to%20Collect%20Memory%20Data%20by%20Using%20the%20Command%20Line.md)|  
|**Attacher à un processus en cours d'exécution**|-   [Applications autonomes .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [Applications Web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [Services .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|  
|**Instrumenter des modules**|-   [Composants autonomes .NET Framework](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-memory-data-with-the-profiler-by-using-the-command-line.md)<br />-   [Applications Web ASP.NET statiquement compilées](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [Applications Web ASP.NET dynamiquement compilées](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [Services .NET](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
##  <a name="BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data"></a> À l'aide de la méthode de concurrence pour collecter des données de conflit de ressources et de migration des données d'activité  
 La méthode de concurrence des outils de profilage vous permet de collecter des données de conflit de ressources et des données d'activité du thread et du processus à partir d'applications multithread.  
  
 Vous pouvez démarrer l'application à l'aide du profileur, ou vous pouvez attacher le profileur à une instance en cours d'exécution d'une application.  
  
|Tâche|Type d'application cible|  
|-----------|------------------------------|  
|**Lancer une application**|-   [Application .NET Framework autonome](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Application native autonome](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Attacher à un processus en cours d'exécution**|-   [Application autonome .NET Framework](../Topic/How%20to:%20Attach%20the%20Profiler%20to%20a%20.NET%20Framework%20Stand-Alone%20Application%20to%20Collect%20Concurrency%20Data%20by%20Using%20the%20Command%20Line.md)<br />-   [Application autonome native](../Topic/How%20to:%20Attach%20the%20Profiler%20to%20a%20Native%20Stand-Alone%20Application%20and%20Collect%20Concurrency%20Data%20by%20Using%20the%20Command%20Line.md)<br />-   [Application Web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Service .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Service natif](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
##  <a name="BKMK_Adding_tier_interaction_data_to_a_profiling_run"></a> Ajout de données sur l'interaction entre les couches à une exécution du profilage  
 Ajout de données sur l'interaction entre les couches à une exécution du profilage requiert des procédures spécifiques avec les outils de profilage de ligne de commande.  Consultez [Collecte de données d’interaction de couche](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
  
## Voir aussi  
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)