---
title: Profilage d’applications web ASP.NET à partir de la ligne de commande | Microsoft Docs
description: Découvrez comment utiliser le Outils de profilage à partir de la ligne de commande pour collecter des données de performances pour les applications Web ASP.NET.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling ASP.NET applications
- profling tools,ASP.NET applications
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: e97e6a3d9115be2b14cac4e87698c6eeb9fc091d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945186"
---
# <a name="command-line-profiling-of-aspnet-web-applications"></a>Profilage d’applications web ASP.NET à partir de la ligne de commande
Cette section décrit les procédures et les options de collecte des données de performances pour les [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] applications Web à l’aide [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de outils de profilage à partir de la ligne de commande.

> [!NOTE]
> Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications UWP nécessitent aussi de nouvelles techniques de collecte. Consultez [Outils d’exécution des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Tâches courantes

| Tâche | Contenu associé |
| - | - |
| **Collecter facilement les données de profilage ASP.NET de base :** utilisez l’outil **VSPerfASPNETCmd** pour collecter des données d’échantillonnage, d’instrumentation, de mémoire .NET, de conflit ou d’interaction de couche, sans la configuration requise et les redémarrages d’Internet Information Services (IIS) qui sont nécessaires à **VSPerfCmd**. **VSPerfASPNETCmd** ne permet pas de collecter des données supplémentaires ni de contrôler la collecte des données. **Remarque :**  **VSPerfASPNETCmd** est l’outil recommandé pour utiliser le profileur autonome pour profiler des sites Web ASP.net. | -   [Profilage de site Web rapide avec VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md) |
| **Collecter des statistiques d’application** : Utilisez la méthode d’échantillonnage pour collecter les statistiques de performance. Les données d’échantillonnage sont utiles pour analyser les problèmes d’utilisation du processeur et pour comprendre les caractéristiques des performances générales d’une application. | -   [Collecter des statistiques d’applications en utilisant l’échantillonnage](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md) |
| **Collecter des données de minutage détaillées** : utilisez la méthode d’instrumentation pour collecter les données de minutage détaillées. Les données d’instrumentation sont utiles pour analyser les problèmes d’E/S et pour analyser de manière plus approfondie les scénarios d’application. | -   [Collecter les données temporelles détaillées à l’aide de l’instrumentation](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md) |
| **Collecter les données de mémoire .NET** : utilisez la méthode d’échantillonnage ou d’instrumentation pour collecter des données d’allocation de mémoire .NET indiquant le nombre d’objets alloués, ainsi que leur taille. Vous pouvez également collecter des données de durée de vie des objets qui indiquent le nombre et la taille des objets qui sont récupérés dans chaque génération de garbage collection. | -   [Collecter des données de mémoire](../profiling/collecting-memory-data-from-an-aspnet-web-application.md) |
| **Collecter des données concurrentielles** : utilisez la méthode d’accès concurrentiel pour collecter les données de conflit de ressources. **Remarque :**  La collecte des données d’activité et de visualisation des threads n’est pas prise en charge pour les applications Web. | -   [Collecter les données d’accès concurrentiel](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md) |
| **Ajouter les données d’interaction de couche :** Vous pouvez ajouter des données de performances sur [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] les appels synchrones que l' [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] application Web effectue dans une [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] base de données Microsoft. | -   [Collecter les données d’interaction de couche](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>Tâches associées

|Tâche|Contenu associé|
|----------|---------------------|
|**Profiler des applications autonomes (clientes)**|-   [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)|
|**Profiler des services**|-   [Services de profil](../profiling/command-line-profiling-of-services.md)|
