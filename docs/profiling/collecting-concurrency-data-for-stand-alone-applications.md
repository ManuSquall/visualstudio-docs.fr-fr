---
title: Collecte de données concurrentielles pour les applications autonomes en utilisant la ligne de commande du profileur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- profiling tools,concurrency method
ms.assetid: 0a2c6d8a-50b3-48aa-b617-9137b049d21e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d50f99fd59406340b47463f8be16e16c552316af
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2018
---
# <a name="collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Collecte de données concurrentielles pour les applications autonomes en utilisant la ligne de commande du profileur
La méthode d’accès concurrentiel des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] permet de collecter des données de conflit de ressources et des données d’activité de thread montrant l’utilisation du processeur, les conflits de threads, la migration des threads, les délais de synchronisation, les zones d’E/S avec chevauchement, et autres événements système.  
  
## <a name="common-tasks"></a>Tâches courantes  
  
|Tâche|Contenu connexe|  
|----------|---------------------|  
|**Démarrer une application .NET Framework et profiler des données concurrentielles**|-   [Guide pratique pour lancer une application .NET Framework pour collecter des données concurrentielles](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)|  
|**Démarrer une application C/C++ et profiler des données concurrentielles**|-   [Guide pratique pour lancer une application native pour collecter des données concurrentielles](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Attacher le profileur à une application .NET Framework en cours d’exécution**|-   [Guide pratique pour attacher le profileur à une application .NET Framework pour collecter des données concurrentielles](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)|  
|**Attacher le profileur à une application C/C++ en cours d’exécution**|-   [Guide pratique pour attacher le profileur à une application native et collecter des données concurrentielles](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-concurrency-data-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>Tâches connexes  
  
### <a name="profiling-stand-alone-applications"></a>Profilage d'applications autonomes  
  
|Tâche|Contenu connexe|  
|----------|---------------------|  
|**Profiler à l’aide de la méthode d’échantillonnage**|-   [Collecte de statistiques d’applications en utilisant l’échantillonnage](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|  
|**Profiler à l’aide de la méthode d’instrumentation**|-   [Collecte de données de minutage détaillées à l’aide de l’instrumentation](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|  
|**Profiler l’allocation de mémoire .NET et le garbage collection**|-   [Collecte de données de mémoire .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|  
|**Ajout d’interactions de couche**|-   [Collecte de données d’interaction de couche](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
### <a name="profiling-concurrency-issues"></a>Profilage des problèmes de concurrence  
  
|Tâche|Contenu connexe|  
|----------|---------------------|  
|**Profiler des applications ASP.NET**|-   [Collecte de données concurrentielles](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|  
|**Profiler des services**|-   [Collecte de données concurrentielles](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
  
### <a name="analyzing-concurrency-data-views-and-reports"></a>Analyse des vues et des rapports de données concurrentielles  
 [Vues de données de conflit de ressources](../profiling/resource-contention-data-views.md)  
  
 [Visualiseur concurrentiel](../profiling/concurrency-visualizer.md)  
  
## <a name="reference"></a>Référence  
 [Informations de référence sur les outils de profilage de ligne de commande](../profiling/command-line-profiling-tools-reference.md)