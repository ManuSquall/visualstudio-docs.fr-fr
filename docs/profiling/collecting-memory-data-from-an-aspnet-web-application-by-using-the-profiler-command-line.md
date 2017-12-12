---
title: "Collecte des données mémoire d’une application web ASP.NET avec la ligne de commande du profileur | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET memory profiling method
- profiling tools,.NET memory method
ms.assetid: 57acf2b0-327a-4c0e-8078-ac2f6d99457d
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ea8dfe604b0038c13b4702bc14e94923cca5b88
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line"></a>Collecte des données de mémoire d’une application web ASP.NET en utilisant la ligne de commande du profileur
Cette section décrit les procédures et les options de collecte des données d’allocation mémoire et de durée de vie des objets pour une application web ASP.NET avec l’outil en ligne de commande **VSPerfCmd**.  
  
> [!NOTE]
>  L’outil **VSPerfCmd** vous permet d’accéder à l’intégralité des fonctionnalités des Outils de profilage, notamment la mise en suspens et la reprise du profilage, ainsi que la collecte de données supplémentaires auprès du processeur et des compteurs de performances Windows. Vous pouvez également utiliser l’outil en ligne de commande **VSPerfASPNETCmd** quand vous n’avez pas besoin de ces fonctionnalités. Par rapport à l’outil en ligne de commande [VSPerfCmd](../profiling/vsperfcmd.md), cet outil ne nécessite ni configuration de variables d’environnement, ni redémarrage de l’ordinateur. Pour plus d’informations, consultez [Profilage de site web rapide avec VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## <a name="common-tasks"></a>Tâches courantes  
  
|Tâche|Contenu associé|  
|----------|---------------------|  
|**Attacher le profileur à une application ASP.NET en cours d’exécution**|-   [Comment : attacher le profileur à une application web ASP.NET pour collecter des données de mémoire](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|  
|**Instrumenter des fichiers binaires compilés statiquement**|-   [Guide pratique pour instrumenter une application ASP.NET compilée statiquement et collecter des données de mémoire](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
|**Instrumenter des fichiers binaires compilés dynamiquement**|-   [Guide pratique pour instrumenter une application ASP.NET compilée dynamiquement et collecter des données de mémoire](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
## <a name="related-tasks"></a>Tâches connexes  
  
### <a name="profiling-aspnet-web-applications"></a>Profilage d'applications Web ASP.NET  
  
|Tâche|Contenu associé|  
|----------|---------------------|  
|**Profiler à l’aide de la méthode d’échantillonnage**|-   [Collecte de statistiques d’applications en utilisant l’échantillonnage](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Profiler à l’aide de la méthode d’instrumentation**|-   [Collecte de données de minutage détaillées à l’aide de l’instrumentation](../profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line.md)|  
|**Profiler le conflit des ressources et l’activité des threads**|-   [Collecte de données concurrentielles](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### <a name="profiling-net-framework-memory-data"></a>Profilage de données de mémoire .NET Framework  
  
|Tâche|Contenu associé|  
|----------|---------------------|  
|**Profiler des applications autonomes (clientes)**|-   [Collecte de données de mémoire .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Profiler des services**|-   [Collecte de données de mémoire .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
  
### <a name="analyzing-net-memory-data-views-and-reports"></a>Analyse des vues et des rapports de données de mémoire .NET  
 [Vues de données de mémoire .NET](../profiling/dotnet-memory-data-views.md)  
  
## <a name="reference"></a>Référence  
 [Référence d’outils de profilage de ligne de commande](../profiling/command-line-profiling-tools-reference.md)