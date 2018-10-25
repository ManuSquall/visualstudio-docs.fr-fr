---
title: Profilage d’applications web ASP.NET à partir de la ligne de commande | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling ASP.NET applications
- profling tools,ASP.NET applications
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 03cb8a6b28ed5f5fece49644d9b1df2608f3e36d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49895663"
---
# <a name="command-line-profiling-of-aspnet-web-applications"></a>Profilage d’applications web ASP.NET à partir de la ligne de commande
Cette section décrit les procédures et les options de collecte des données de performances pour les applications web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] à l’aide des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], à partir de la ligne de commande.  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications UWP nécessitent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Tâches courantes
  
| Tâche | Contenu associé |
| - | - |
| **Collecter facilement les données de profilage ASP.NET de base :** utilisez l’outil **VSPerfASPNETCmd** pour collecter des données d’échantillonnage, d’instrumentation, de mémoire .NET, de conflit ou d’interaction de couche, sans la configuration requise et les redémarrages d’Internet Information Services (IIS) qui sont nécessaires à **VSPerfCmd**. **VSPerfASPNETCmd** ne permet pas de collecter des données supplémentaires ni de contrôler la collecte des données. **Remarque** : **VSPerfASPNETCmd** est l’outil à privilégier quand vous utilisez le profileur autonome pour profiler des sites web ASP.NET. | -   [Profilage de site web rapide avec VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md) |
| **Collecter des statistiques d’application** : Utilisez la méthode d’échantillonnage pour collecter les statistiques de performance. Les données d’échantillonnage sont utiles pour analyser les problèmes d’utilisation du processeur et pour comprendre les caractéristiques des performances générales d’une application. | -   [Collecter des statistiques d’applications en utilisant l’échantillonnage](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md) |
| **Collecter des données de minutage détaillées** : utilisez la méthode d’instrumentation pour collecter les données de minutage détaillées. Les données d’instrumentation sont utiles pour analyser les problèmes d’E/S et pour analyser de manière plus approfondie les scénarios d’application. | -   [Collecter les données temporelles détaillées à l’aide de l’instrumentation](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md) |
| **Collecter les données de mémoire .NET** : utilisez la méthode d’échantillonnage ou d’instrumentation pour collecter des données d’allocation de mémoire .NET indiquant le nombre d’objets alloués, ainsi que leur taille. Vous pouvez également collecter des données de durée de vie des objets qui indiquent le nombre et la taille des objets qui sont récupérés dans chaque génération de garbage collection. | -   [Collecter des données de mémoire](../profiling/collecting-memory-data-from-an-aspnet-web-application.md) |
| **Collecter des données concurrentielles** : utilisez la méthode d’accès concurrentiel pour collecter les données de conflit de ressources. **Remarque** : La collecte des données liées à l’activité des threads et à la visualisation n’est pas possible pour les applications web. | -   [Collecter des données concurrentielles](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md) |
| **Ajouter des données d’interaction de couche** : vous pouvez ajouter des données de performances relatives aux appels [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] synchrones émis par l’application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] vers la base de données Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]. | -   [Collecter les données d’interaction de couche](../profiling/adding-tier-interaction-data-from-the-command-line.md) |
  
## <a name="related-tasks"></a>Tâches connexes

  
|Tâche|Contenu associé|  
|----------|---------------------|  
|**Profiler des applications autonomes (clientes)**|-   [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**Profiler des services**|-   [Profiler des services](../profiling/command-line-profiling-of-services.md)|