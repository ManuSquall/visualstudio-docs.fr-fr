---
title: Obtenir les données de mémoire d’une application web ASP.NET avec la ligne de commande du profileur
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method
- profiling tools,.NET memory method
ms.assetid: 57acf2b0-327a-4c0e-8078-ac2f6d99457d
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 9e8d9fde00a2390793ae8efe05b684e73caca321
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773057"
---
# <a name="collect-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line"></a>Collecter des données de mémoire d’une application web ASP.NET en utilisant la ligne de commande du profileur
Cette section décrit les procédures et les options de collecte des données d’allocation mémoire et de durée de vie des objets pour une application web ASP.NET avec l’outil en ligne de commande **VSPerfCmd**.

> [!NOTE]
> L’outil **VSPerfCmd** vous permet d’accéder à l’intégralité des fonctionnalités des Outils de profilage, notamment la mise en suspens et la reprise du profilage, ainsi que la collecte de données supplémentaires auprès du processeur et des compteurs de performances Windows. Vous pouvez également utiliser l’outil en ligne de commande **VSPerfASPNETCmd** quand vous n’avez pas besoin de ces fonctionnalités. Par rapport à l’outil en ligne de commande [VSPerfCmd](../profiling/vsperfcmd.md), cet outil ne nécessite ni configuration de variables d’environnement, ni redémarrage de l’ordinateur. Pour plus d’informations, voir [profilage du site Web Rapid avec VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Tâches courantes

|Tâche|Contenu associé|
|----------|---------------------|
|**Attacher le profileur à une application ASP.NET en cours d’exécution**|-   [Comment : Attachez le profileur à une application Web ASP.NET pour collecter des données de mémoire](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|
|**Instrumenter des fichiers binaires compilés statiquement**|-   [Comment : Instrument d’une application ASP.NET compilée de façon statique et collectez des données de mémoire](../profiling/how-to-instrument-a-statically-compiled-aspnet-app-and-collect-memory-data.md)|
|**Instrumenter des fichiers binaires compilés dynamiquement**|-   [Comment : Instrumenter une application ASP.NET compilée dynamiquement et collecter des données de mémoire](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)|

## <a name="related-tasks"></a>Tâches associées

### <a name="profile-aspnet-web-applications"></a>Profiler des applications web ASP.NET

|Tâche|Contenu associé|
|----------|---------------------|
|**Profiler à l’aide de la méthode d’échantillonnage**|-   [Collecter des statistiques d’applications en utilisant l’échantillonnage](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Profiler à l’aide de la méthode d’instrumentation**|-   [Collecter les données temporelles détaillées à l’aide de l’instrumentation](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|
|**Profiler le conflit des ressources et l’activité des threads**|-   [Recueillir des données de concurrence](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="profile-net-framework-memory-data"></a>Profiler des données de mémoire .NET Framework

|Tâche|Contenu associé|
|----------|---------------------|
|**Profiler des applications autonomes (clientes)**|-   [Collecter des données de mémoire .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Profiler des services**|-   [Recueillir des données de mémoire .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|

### <a name="analyze-net-memory-data-views-and-reports"></a>Analyser des vues et des rapports de données de mémoire .NET
- [vues de données de mémoire .NET](../profiling/dotnet-memory-data-views.md)

## <a name="reference"></a>Informations de référence
- [Référence des outils de profilage de la ligne de commandement](../profiling/command-line-profiling-tools-reference.md)
