---
title: Collecter des statistiques d’application en utilisant la méthode d’échantillonnage du profileur
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 07840ab2-3a92-4744-ac87-48b19e0ceecd
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 17217a51c58e1d30b6e6854ee9dbb0c1fb662a3a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779686"
---
# <a name="collect-application-statistics-for-services-by-using-the-profiler-sampling-method"></a>Collecter des statistiques d’application des services en utilisant la méthode d’échantillonnage du profileur
Cette section décrit les procédures et les options de collecte des statistiques de performances des services Windows utilisant la méthode d’échantillonnage à partir de la ligne de commande.

> [!NOTE]
> Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications UWP nécessitent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Tâches courantes

|Tâche|Contenu associé|
|----------|---------------------|
|**Attacher le profileur à un service .NET**|-   [Comment : Joindre le profileur à un service .NET pour recueillir des statistiques d’application](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)|
|**Ajouter des interactions de couche**|-   [Recueillir des données d’interaction de niveau](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**Attacher le profileur à un service C/C++**|-   [Comment : Joindre le profileur à un service autochtone pour recueillir des statistiques d’application](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="related-tasks"></a>Tâches associées

### <a name="profile-windows-services"></a>Profiler des services Windows

|Tâche|Contenu associé|
|----------|---------------------|
|**Profiler à l’aide de la méthode d’instrumentation**|-   [Collecter les données temporelles détaillées à l’aide de l’instrumentation](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|
|**Profiler l’allocation de mémoire .NET et le garbage collection**|-   [Recueillir des données de mémoire .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|
|**Profiler le conflit des ressources et l’activité des threads**|-   [Recueillir des données de concurrence](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|

### <a name="profile-by-using-the-sampling-method"></a>Profiler à l’aide de la méthode d’échantillonnage

|Tâche|Contenu associé|
|----------|---------------------|
|**Profiler des applications autonomes (clientes)**|-   [Collecter des statistiques d’applications en utilisant l’échantillonnage](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|**Profiler des applications web ASP.NET**|-   [Collecter des statistiques d’applications en utilisant l’échantillonnage](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|

### <a name="analyze-sampling-data-views-and-reports"></a>Analyser des vues et des rapports de données d’échantillonnage
- [Vues de données sur les méthodes d’échantillonnage](../profiling/profiler-sampling-method-data-views.md)
