---
title: Collecte de statistiques d’applications pour des applications autonomes en utilisant la ligne de commande du profileur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method
- profilng tools,sampling method
ms.assetid: be2dbdd0-fc88-45f9-a1d5-bcb4f64e17ad
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 03e27d021b8b3c5ec29a8646a1bbe7bc6ebdecc0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839937"
---
# <a name="collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Collecte de statistiques d’applications pour des applications autonomes en utilisant la ligne de commande du profileur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette section décrit les procédures et les options de collecte des statistiques de performances d’une application cliente (autonome) utilisant la méthode d’échantillonnage à partir de la ligne de commande.  
  
> [!NOTE]
> Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications Windows Store demandent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Tâches courantes  
  
|Tâche|Contenu connexe|  
|----------|---------------------|  
|**Démarrer une application à l’aide du profilage**|-   [Comment : lancer une application autonome et collecter des statistiques d’applications](../profiling/how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Attacher le profileur à une application .NET Framework en cours d’exécution**|-   [Comment : attacher le profileur à une application de .NET Framework et collecter des statistiques d’applications](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Attacher le profileur à une application C/C++ en cours d’exécution**|-   [Comment : attacher le profileur à une application native et collecter des statistiques d’applications](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Ajouter des interactions de couche**|-   [Collecte des données d’interaction de couche](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## <a name="related-tasks"></a>Tâches associées  
  
### <a name="profiling-stand-alone-applications"></a>Profilage d'applications autonomes  
  
|Tâche|Contenu connexe|  
|----------|---------------------|  
|**Instrumenter une application**|-   [Collecte de données de temporisation détaillées à l’aide de l’instrumentation](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Collecter des données relatives à l’allocation de mémoire .NET et au garbage collection**|-   [Collecte des données de mémoire .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Collecter les données relatives aux conflits de ressources et à l’exécution des threads**|-   [Collecte de données de concurrence](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
  
### <a name="profiling-by-using-the-sampling-method"></a>Profilage à l’aide de la méthode d’échantillonnage  
  
|Tâche|Contenu connexe|  
|----------|---------------------|  
|**Profiler des applications web ASP.NET**|-   [Collecte des statistiques d’application à l’aide de l’échantillonnage](/visualstudio/profiling/collecting-concurrency-data-for-an-aspnet-web-application?view=vs-2015)|  
|**Profiler des services**|-   [Collecte des statistiques d’application à l’aide de l’échantillonnage](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md). Explique comment collecter les statistiques de performances à partir des services de Windows à l’aide de la méthode d’échantillonnage.|  
  
### <a name="analyzing-sampling-data-views-and-reports"></a>Analyse des vues et des rapports de données d’échantillonnage  
 [Vues de données de la méthode d’échantillonnage](../profiling/profiler-sampling-method-data-views.md)
