---
title: Profilage d’applications web ASP.NET à partir de la ligne de commande | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- profiling ASP.NET applications
- profling tools,ASP.NET applications
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5436da548acaf16169437fdc98b51d182891d2d9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51759151"
---
# <a name="command-line-profiling-of-aspnet-web-applications"></a>Profilage d’applications web ASP.NET à partir de la ligne de commande
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette section décrit les procédures et les options de collecte des données de performances pour les applications web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] à l’aide des outils de profilage [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], à partir de la ligne de commande.  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications Windows Store demandent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Tâches courantes  
  
|Tâche|Contenu associé|  
|----------|---------------------|  
|**Collecter facilement les données de profilage ASP.NET de base :** utilisez l’outil **VSPerfASPNETCmd** pour collecter des données d’échantillonnage, d’instrumentation, de mémoire .NET, de conflit ou d’interaction de couche, sans la configuration requise et les redémarrages d’Internet Information Services (IIS) qui sont nécessaires à **VSPerfCmd**. **VSPerfASPNETCmd** ne permet pas de collecter des données supplémentaires ni de contrôler la collecte des données. **Remarque** : **VSPerfASPNETCmd** est l’outil à privilégier quand vous utilisez le profileur autonome pour profiler des sites web ASP.NET.|-   [Profilage de site web rapide avec VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)|  
|**Collecter des statistiques d’application** : Utilisez la méthode d’échantillonnage pour collecter les statistiques de performance. Les données d’échantillonnage sont utiles pour analyser les problèmes d’utilisation du processeur et pour comprendre les caractéristiques des performances générales d’une application.|-   [Collecte de statistiques d’applications en utilisant l’échantillonnage](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Collecter des données de minutage détaillées** : utilisez la méthode d’instrumentation pour collecter les données de minutage détaillées. Les données d’instrumentation sont utiles pour analyser les problèmes d’E/S et pour analyser de manière plus approfondie les scénarios d’application.|-   [Collecte de données de temporisation détaillées à l’aide de l’instrumentation](../profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line.md)|  
|**Collecter les données de mémoire .NET** : utilisez la méthode d’échantillonnage ou d’instrumentation pour collecter des données d’allocation de mémoire .NET indiquant le nombre d’objets alloués, ainsi que leur taille. Vous pouvez également collecter des données de durée de vie des objets qui indiquent le nombre et la taille des objets qui sont récupérés dans chaque génération de garbage collection.|-   [Collecte des données de mémoire](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**Collecter des données concurrentielles** : utilisez la méthode d’accès concurrentiel pour collecter les données de conflit de ressources. **Remarque** : La collecte des données liées à l’activité des threads et à la visualisation n’est pas possible pour les applications web.|-   [Collecte de données de concurrence](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
|**Ajouter des données d’interaction de couche** : vous pouvez ajouter des données de performances relatives aux appels [!INCLUDE[vstecado](../includes/vstecado-md.md)] synchrones émis par l’application web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] vers la base de données Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|-   [Collecte de données d’interaction de couche](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## <a name="related-tasks"></a>Tâches connexes  
  
|Tâche|Contenu associé|  
|----------|---------------------|  
|**Profiler des applications autonomes (clientes)**|-   [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**Profiler des services**|-   [Profilage des services](../profiling/command-line-profiling-of-services.md)|



