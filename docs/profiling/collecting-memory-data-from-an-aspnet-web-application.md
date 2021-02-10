---
title: Ligne de commande du profileur-récupération des données de mémoire de l’application Web ASP.NET
description: Découvrez comment utiliser l’outil en ligne de commande VSPerfCmd pour collecter l’allocation de mémoire et la date de durée de vie des objets pour une application Web ASP.NET.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- .NET memory profiling method
- profiling tools,.NET memory method
ms.assetid: 57acf2b0-327a-4c0e-8078-ac2f6d99457d
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: edcac130a37b90f164cc2b90c11fe43adeea8414
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949400"
---
# <a name="collect-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line"></a>Collecter des données de mémoire d’une application web ASP.NET en utilisant la ligne de commande du profileur
Cette section décrit les procédures et les options permettant de collecter les données d’allocation de mémoire et de durée de vie des objets pour une application Web ASP.NET à l’aide de l’outil en ligne de commande **VSPerfCmd** .

> [!NOTE]
> L’outil **VSPerfCmd** vous permet d’accéder à l’intégralité des fonctionnalités des Outils de profilage, notamment la mise en suspens et la reprise du profilage, ainsi que la collecte de données supplémentaires auprès du processeur et des compteurs de performances Windows. Vous pouvez également utiliser l’outil en ligne de commande **VSPerfASPNETCmd** quand vous n’avez pas besoin de ces fonctionnalités. Par rapport à l’outil en ligne de commande [VSPerfCmd](../profiling/vsperfcmd.md), cet outil ne nécessite ni configuration de variables d’environnement, ni redémarrage de l’ordinateur. Pour plus d’informations, consultez [profilage de site Web rapide avec VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Tâches courantes

|Tâche|Contenu associé|
|----------|---------------------|
|**Attacher le profileur à une application ASP.NET en cours d’exécution**|-   [Comment : attacher le profileur à une application Web ASP.NET pour collecter des données de mémoire](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|
|**Instrumenter des fichiers binaires compilés statiquement**|-   [Comment : instrumenter une application ASP.NET compilée statiquement et collecter des données de mémoire](../profiling/how-to-instrument-a-statically-compiled-aspnet-app-and-collect-memory-data.md)|
|**Instrumenter des fichiers binaires compilés dynamiquement**|-   [Comment : instrumenter une application ASP.NET compilée dynamiquement et collecter des données de mémoire](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)|

## <a name="related-tasks"></a>Tâches associées

### <a name="profile-aspnet-web-applications"></a>Profiler des applications web ASP.NET

|Tâche|Contenu associé|
|----------|---------------------|
|**Profiler à l’aide de la méthode d’échantillonnage**|-   [Collecter des statistiques d’applications en utilisant l’échantillonnage](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Profiler à l’aide de la méthode d’instrumentation**|-   [Collecter les données temporelles détaillées à l’aide de l’instrumentation](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|
|**Profiler le conflit des ressources et l’activité des threads**|-   [Collecter les données d’accès concurrentiel](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="profile-net-framework-memory-data"></a>Profiler des données de mémoire .NET Framework

|Tâche|Contenu associé|
|----------|---------------------|
|**Profiler des applications autonomes (clientes)**|-   [Collecter des données de mémoire .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Profiler des services**|-   [Collecter les données de mémoire .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|

### <a name="analyze-net-memory-data-views-and-reports"></a>Analyser des vues et des rapports de données de mémoire .NET
- [Vues de données de mémoire .NET](../profiling/dotnet-memory-data-views.md)

## <a name="reference"></a>Référence
- [Informations de référence sur les outils de profilage de la ligne de commande](../profiling/command-line-profiling-tools-reference.md)
