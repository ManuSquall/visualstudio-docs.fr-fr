---
title: 'Ligne de commande du profileur : collecter les statistiques des applications autonomes'
description: Collectez les statistiques d’application pour les applications autonomes en utilisant la ligne de commande du profileur dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- sampling profiling method
- profilng tools,sampling method
ms.assetid: be2dbdd0-fc88-45f9-a1d5-bcb4f64e17ad
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 053f846b15968ad7a5714f99779944bd63a8b6d3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868385"
---
# <a name="collect-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Collecter des statistiques d’applications pour des applications autonomes en utilisant la ligne de commande du profileur
Cette section décrit les procédures et les options de collecte des statistiques de performances d’une application cliente (autonome) utilisant la méthode d’échantillonnage à partir de la ligne de commande.

> [!NOTE]
> Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications UWP nécessitent aussi de nouvelles techniques de collecte. Consultez [Outils d’exécution des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Tâches courantes

|Tâche|Contenu connexe|
|----------|---------------------|
|**Démarrer une application à l’aide du profilage**|-   [Comment : lancer une application autonome et collecter des statistiques d’applications](../profiling/how-to-launch-a-stand-alone-app-and-collect-application-statistics.md)|
|**Attacher le profileur à une application .NET Framework en cours d’exécution**|-   [Comment : attacher le profileur à une application de .NET Framework et collecter des statistiques d’applications](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)|
|**Attacher le profileur à une application C/C++ en cours d’exécution**|-   [Comment : attacher le profileur à une application native et collecter des statistiques d’applications](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-application-statistics.md)|
|**Ajouter des interactions de couche**|-   [Collecte des données d’interaction de couche](../profiling/adding-tier-interaction-data-from-the-command-line.md)|

## <a name="related-tasks"></a>Tâches associées

### <a name="profile-stand-alone-applications"></a>Profiler des applications autonomes

|Tâche|Contenu connexe|
|----------|---------------------|
|**Instrumenter une application**|-   [Collecter les données temporelles détaillées à l’aide de l’instrumentation](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**Collecter des données relatives à l’allocation de mémoire .NET et au garbage collection**|-   [Collecter des données de mémoire .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Collecter les données relatives aux conflits de ressources et à l’exécution des threads**|-   [Collecter les données d’accès concurrentiel](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|

### <a name="profile-by-using-the-sampling-method"></a>Profiler à l’aide de la méthode d’échantillonnage

|Tâche|Contenu connexe|
|----------|---------------------|
|**Profiler des applications Web ASP.NET**|-   [Collecter des statistiques d’applications en utilisant l’échantillonnage](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Profiler des services**|-   [Collecter des statistiques d’applications à l’aide de l’échantillonnage](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md). Explique comment collecter les statistiques de performances à partir des services de Windows à l’aide de la méthode d’échantillonnage.|

### <a name="analyze-sampling-data-views-and-reports"></a>Analyser des vues et des rapports de données d’échantillonnage
- [Vues de données de la méthode d’échantillonnage](../profiling/profiler-sampling-method-data-views.md)
