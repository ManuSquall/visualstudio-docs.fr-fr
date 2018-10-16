---
title: Collecte de données concurrentielles pour un service en utilisant la ligne de commande du profileur | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 275aacba-b2af-4d34-8931-ee30d777a256
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a783c30c575bbf2f55b4c31840392e7e213940e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49250976"
---
# <a name="collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line"></a>Collecte de données concurrentielles pour un service en utilisant la ligne de commande du profileur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La méthode d’accès concurrentiel des outils de profilage [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] permet de collecter des données de conflit de ressources et des données d’activité de thread montrant l’utilisation du processeur, les conflits de threads, la migration des threads, les délais de synchronisation, les zones d’E/S avec chevauchement, et autres événements système.  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications Windows Store demandent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Tâches courantes  
  
|Tâche|Contenu associé|  
|----------|---------------------|  
|**Attacher le profileur à un service .NET en cours d’exécution**|-   [Guide pratique pour attacher le profileur à un service .NET pour collecter des données concurrentielles](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Ajouter des interactions de couche**|-   [Collecte de données d’interaction de couche](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**Attacher le profileur à un service C/C++ en cours d’exécution**|-   [Guide pratique pour attacher le profileur à un service natif pour collecter des données concurrentielles](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>Tâches connexes  
  
### <a name="profiling-windows-services"></a>Profilage des services Windows  
  
|Tâche|Contenu associé|  
|----------|---------------------|  
|**Profiler à l’aide de la méthode d’échantillonnage**|-   [Collecte de statistiques d’applications en utilisant l’échantillonnage](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
|**Profiler à l’aide de la méthode d’instrumentation**|-   [Collecte de données de temporisation détaillées à l’aide de l’instrumentation](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
|**Profiler l’allocation de mémoire .NET et le garbage collection**|-   [Collecte de données de mémoire .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
  
### <a name="profiling-concurrency-data"></a>Profilage des données concurrentielles  
  
|Tâche|Contenu associé|  
|----------|---------------------|  
|**Profiler des applications autonomes**|-   [Collecte de données de concurrence](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Profiler des applications web ASP.NET**|-   [Collecte de données de concurrence](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### <a name="analyzing-concurrency-data-views-and-reports"></a>Analyse des vues et des rapports de données concurrentielles  
 [Vues de données de conflit de ressources](../profiling/resource-contention-data-views.md)  
  
 [Visualiseur concurrentiel](../profiling/concurrency-visualizer.md)  
  
## <a name="reference"></a>Référence  
 [Informations de référence sur les outils de profilage de ligne de commande](../profiling/command-line-profiling-tools-reference.md)



