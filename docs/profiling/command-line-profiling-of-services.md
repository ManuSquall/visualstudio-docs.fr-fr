---
title: Profilage de services à partir de la ligne de commande | Microsoft Docs
description: Découvrez comment utiliser le Outils de profilage à partir de la ligne de commande pour collecter les données de performances des services Windows.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling toos,services
- profiling services
ms.assetid: f0d62318-b0e8-49c6-9a30-9f7a6adef2f6
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: dd77161184c5cb8be89ed522bbf06b6d80ca4bee
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969501"
---
# <a name="command-line-profiling-of-services"></a>Profilage de services à partir de la ligne de commande
Cette section décrit les procédures et les options de collecte des données de performances des services Windows utilisant les outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] à partir de la ligne de commande.

> [!NOTE]
> Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications UWP nécessitent aussi de nouvelles techniques de collecte. Consultez [Outils d’exécution des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Tâches courantes

| Tâche | Contenu associé |
| - | - |
| **Collecter des statistiques d’application** : Utilisez la méthode d’échantillonnage pour collecter les statistiques de performance. Les données d’échantillonnage sont utiles pour analyser les problèmes d’utilisation du processeur et pour comprendre les caractéristiques des performances générales d’une application. | -   [Collecter des statistiques d’applications en utilisant l’échantillonnage](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md) |
| **Collecter des données de minutage détaillées** : utilisez la méthode d’instrumentation pour collecter les données de minutage détaillées. Les données d’instrumentation sont utiles pour analyser les problèmes d’E/S et pour analyser de manière plus approfondie les scénarios d’application. | -   [Collecter les données temporelles détaillées à l’aide de l’instrumentation](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md) |
| **Collecter les données de mémoire .NET** : utilisez la méthode d’échantillonnage ou d’instrumentation pour collecter des données d’allocation de mémoire .NET indiquant le nombre d’objets alloués, ainsi que leur taille. Vous pouvez également collecter des données de durée de vie des objets qui indiquent le nombre et la taille des objets qui sont récupérés dans chaque génération de garbage collection. | -   [Collecter les données de mémoire .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md) |
| **Collecter les données d’accès concurrentiel :** Utilisez la méthode d’accès concurrentiel pour collecter des données de conflit de ressources et des données d’activité de thread qui indiquent l’utilisation de l’UC, la contention des threads, la migration des threads, les délais de synchronisation, les zones d’e/s avec chevauchement et d’autres événements système. | -   [Collecter les données d’accès concurrentiel](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md) |
| **Ajouter des données d’interaction de couche** : vous pouvez ajouter des données de performances relatives aux appels ADO.NET synchrones émis par le service vers une base de données Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]. | -   [Collecter les données d’interaction de couche](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>Tâches associées

|Tâche|Contenu associé|
|----------|---------------------|
|**Profiler des applications autonomes (clientes)**|-   [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)|
|**Profiler des applications ASP.NET**|-   [Profiler des applications Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
