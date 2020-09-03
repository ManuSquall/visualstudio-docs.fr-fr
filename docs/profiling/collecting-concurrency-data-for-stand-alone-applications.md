---
title: Ligne de commande du profileur pour obtenir des données d’accès concurrentiel d’une application autonome
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- concurrency profiling method
- profiling tools,concurrency method
ms.assetid: 0a2c6d8a-50b3-48aa-b617-9137b049d21e
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 15e8be092a8e1e065f2aa1a80be7447a370974b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85331870"
---
# <a name="collect-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Collecter des données concurrentielles pour les applications autonomes en utilisant la ligne de commande du profileur
La méthode d’accès concurrentiel des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] permet de collecter des données de conflit de ressources et des données d’activité de thread montrant l’utilisation du processeur, les conflits de threads, la migration des threads, les délais de synchronisation, les zones d’E/S avec chevauchement, et autres événements système.

## <a name="common-tasks"></a>Tâches courantes

|Tâche|Contenu connexe|
|----------|---------------------|
|**Démarrer une application .NET Framework et profiler des données concurrentielles**|-   [Comment : lancer une application de .NET Framework pour collecter des données d’accès concurrentiel](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)|
|**Démarrer une application C/C++ et profiler des données concurrentielles**|-   [Comment : lancer une application native pour collecter des données d’accès concurrentiel](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|
|**Attacher le profileur à une application .NET Framework en cours d’exécution**|-   [Comment : attacher le profileur à une application de .NET Framework pour collecter des données d’accès concurrentiel](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)|
|**Attacher le profileur à une application C/C++ en cours d’exécution**|-   [Comment : attacher le profileur à une application native et collecter des données d’accès concurrentiel](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)|

## <a name="related-tasks"></a>Tâches associées

### <a name="profile-stand-alone-applications"></a>Profiler des applications autonomes

|Tâche|Contenu connexe|
|----------|---------------------|
|**Profiler à l’aide de la méthode d’échantillonnage**|-   [Collecter des statistiques d’applications en utilisant l’échantillonnage](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|**Profiler à l’aide de la méthode d’instrumentation**|-   [Collecter les données temporelles détaillées à l’aide de l’instrumentation](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**Profiler l’allocation de mémoire .NET et le garbage collection**|-   [Collecter des données de mémoire .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Ajouter des interactions de couche**|-   [Collecter les données d’interaction de couche](../profiling/adding-tier-interaction-data-from-the-command-line.md)|

### <a name="profile-concurrency-issues"></a>Profiler des problèmes de concurrence

|Tâche|Contenu connexe|
|----------|---------------------|
|**Profiler des applications ASP.NET**|-   [Collecter les données d’accès concurrentiel](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|
|**Profiler des services**|-   [Collecter les données d’accès concurrentiel](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>Analyser des vues et des rapports de données concurrentielles
- [Vues de données de conflit de ressources](../profiling/resource-contention-data-views.md)

- [Visualiseur concurrentiel](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>Informations de référence
- [Informations de référence sur les outils de profilage de la ligne de commande](../profiling/command-line-profiling-tools-reference.md)
