---
title: Profilage d’applications autonomes à partir de la ligne de commande | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profillng tools,stand-alone applications
- profling stand-alone applications
ms.assetid: a47f2bf2-186d-4120-bb79-34e2f3a1ee42
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bcd48f421dcae74e82b0d9249a958f2a834f0a45
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56603285"
---
# <a name="command-line-profiling-of-stand-alone-applications"></a>Profilage d’applications autonomes à partir de la ligne de commande
Cette section décrit les procédures et les options de collecte des données de performances pour les applications autonomes (clientes) à l’aide des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], à partir de la ligne de commande.

## <a name="common-tasks"></a>Tâches courantes

| Tâche | Contenu connexe |
| - | - |
| **Collecter des statistiques d’applications :** utiliser la méthode d’échantillonnage pour collecter les statistiques de performances. Les données d’échantillonnage sont utiles pour analyser les problèmes d’utilisation du processeur et pour comprendre les caractéristiques des performances générales d’une application. | -   [Collecter des statistiques d’applications en utilisant l’échantillonnage](../profiling/collecting-application-statistics-for-stand-alone-applications.md) |
| **Collecter des données de temporisation détaillées :** utiliser la méthode d’instrumentation pour collecter des information de temporisation détaillées. Les données d’instrumentation sont utiles pour analyser les problèmes d’E/S et pour analyser de manière plus approfondie les scénarios d’application. | -   [Collecter les données temporelles détaillées à l’aide de l’instrumentation](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md) |
| **Collecter les données de mémoire .NET :** utiliser la méthode d’échantillonnage ou d’instrumentation pour collecter des données d’allocation de mémoire .NET indiquant le nombre d’objets alloués et leur taille. Vous pouvez également collecter des données de durée de vie des objets qui indiquent le nombre et la taille des objets qui sont récupérés dans chaque génération de garbage collection. | -   [Collecter des données de mémoire .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md) |
| **Collecter des données concurrentielles** : utiliser la méthode d’accès concurrentiel pour collecter des données de conflit de ressources et des données d’activité de thread montrant l’utilisation du processeur, les conflits de threads, la migration des threads, les délais de synchronisation, les zones d’E/S avec chevauchement, et autres événements système. | -   [Collecter des données concurrentielles](../profiling/collecting-concurrency-data-for-stand-alone-applications.md) |
| **Ajouter des données d’interaction de couche :** vous pouvez ajouter des données de performances relatives aux appels ADO.NET synchrones émis par l’application vers une base de données Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]. Pour ajouter des données d’interaction de couche à une exécution de profilage, vous devez utiliser des procédures spécifiques avec les outils de profilage en ligne de commande. | -   [Collecter les données d’interaction de couche](../profiling/adding-tier-interaction-data-from-the-command-line.md) |
| **Faites un essai** : utiliser des procédures pas à pas pour profiler un exemple d’application cliente à l’aide de la méthode d’échantillonnage ou d’instrumentation. | -   [Procédure pas à pas : Profilage en ligne de commande avec l’échantillonnage](../profiling/walkthrough-command-line-profiling-using-sampling.md)<br />-   [Procédure pas à pas : Profilage de la ligne de commande à l’aide de l’instrumentation](/visualstudio/profiling/command-line-profiling-of-stand-alone-applications) |

## <a name="related-tasks"></a>Tâches connexes

|Tâche|Contenu associé|
|----------|---------------------|
|**Profiler des applications ASP.NET**|-   [Profiler des applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
|**Profiler des services**|-   [Profiler des services](../profiling/command-line-profiling-of-services.md)|