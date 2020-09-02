---
title: Collecte de données concurrentielles pour les applications autonomes en utilisant la ligne de commande du profileur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- profiling tools,concurrency method
ms.assetid: 0a2c6d8a-50b3-48aa-b617-9137b049d21e
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7fac1c840d93c03b659e7934a82eb53895b60ede
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68141940"
---
# <a name="collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Collecte de données concurrentielles pour les applications autonomes en utilisant la ligne de commande du profileur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La méthode d’accès concurrentiel des outils de profilage [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] permet de collecter des données de conflit de ressources et des données d’activité de thread montrant l’utilisation du processeur, les conflits de threads, la migration des threads, les délais de synchronisation, les zones d’E/S avec chevauchement, et autres événements système.  
  
## <a name="common-tasks"></a>Tâches courantes  
  
|Tâche|Contenu connexe|  
|----------|---------------------|  
|**Démarrer une application .NET Framework et profiler des données concurrentielles**|-   [Guide pratique pour lancer une application .NET Framework pour collecter des données concurrentielles](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Démarrer une application C/C++ et profiler des données concurrentielles**|-   [Comment : lancer une application native pour collecter des données d’accès concurrentiel](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Attacher le profileur à une application .NET Framework en cours d’exécution**|-   [Comment : attacher le profileur à une application de .NET Framework pour collecter des données d’accès concurrentiel](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Attacher le profileur à une application C/C++ en cours d’exécution**|-   [Comment : attacher le profileur à une application native et collecter des données d’accès concurrentiel](/visualstudio/profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data?view=vs-2015)|  
  
## <a name="related-tasks"></a>Tâches associées  
  
### <a name="profiling-stand-alone-applications"></a>Profilage d'applications autonomes  
  
|Tâche|Contenu connexe|  
|----------|---------------------|  
|**Profiler à l’aide de la méthode d’échantillonnage**|-   [Collecte des statistiques d’application à l’aide de l’échantillonnage](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Profiler à l’aide de la méthode d’instrumentation**|-   [Collecte de données de temporisation détaillées à l’aide de l’instrumentation](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Profiler l’allocation de mémoire .NET et le garbage collection**|-   [Collecte des données de mémoire .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Ajout d’interactions de couche**|-   [Collecte des données d’interaction de couche](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
### <a name="profiling-concurrency-issues"></a>Profilage des problèmes de concurrence  
  
|Tâche|Contenu connexe|  
|----------|---------------------|  
|**Profiler des applications ASP.NET**|-   [Collecte de données de concurrence](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
|**Profiler des services**|-   [Collecte de données de concurrence](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
  
### <a name="analyzing-concurrency-data-views-and-reports"></a>Analyse des vues et des rapports de données concurrentielles  
 [Vues de données de conflit de ressources](../profiling/resource-contention-data-views.md)  
  
 [Visualiseur concurrentiel](../profiling/concurrency-visualizer.md)  
  
## <a name="reference"></a>Référence  
 [Référence des Outils de profilage de ligne de commande](../profiling/command-line-profiling-tools-reference.md)
