---
title: Collecter des statistiques pour des applications web ASP.NET | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling tools, sampling method
- sampling profling method
ms.assetid: f8383ab1-eb49-4d3f-8608-d8b4d51a81be
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: aspnet
ms.openlocfilehash: e567d6afb0d7e778dcc656e633ba4a670eb2ecea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="collect-statistics-for-aspnet-web-apps"></a>Collecter des statistiques pour des applications web ASP.NET

Cette section décrit les procédures et les options de collecte des statistiques de performances pour une application web ASP.NET à l’aide des outils en ligne de commande **VSPerfASPNETCmd** et **VSPerfCmd**, et de la méthode de profilage par échantillonnage.  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications UWP nécessitent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
> [!NOTE]
>  Même si l’outil **VSPerfCmd** vous permet d’accéder à l’intégralité des fonctionnalités des outils de profilage, y compris la suspension et la reprise du profilage, ainsi que la collecte de données supplémentaires à partir du processeur et des compteurs de performances Windows, vous devez utiliser l’outil en ligne de commande **VSPerfASPNETCmd** si vous n’avez pas besoin de ces fonctionnalités. L’outil en ligne de commande **VSPerfASPNETCmd** est recommandé quand vous profilez des sites web ASP.NET à l’aide du profileur autonome. Par rapport à l’outil en ligne de commande [VSPerfCmd](../profiling/vsperfcmd.md), cet outil ne nécessite ni configuration de variables d’environnement, ni redémarrage de l’ordinateur. Pour plus d’informations, consultez [Profilage de site web rapide avec VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## <a name="common-tasks"></a>Tâches courantes  
  
|Tâche|Contenu associé|  
|----------|---------------------|  
|**Attacher le profileur à une application ASP.NET**|-   [Guide pratique pour attacher le profileur à une application web ASP.NET pour collecter des statistiques d’applications](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>Tâches connexes  
  
### <a name="profiling-aspnet-web-applications"></a>Profilage d'applications Web ASP.NET  
  
|Tâche|Contenu associé|  
|----------|---------------------|  
|**Profiler à l’aide de la méthode d’instrumentation**|-   [Collecte de données de temporisation détaillées à l’aide de l’instrumentation](../profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line.md)|  
|**Profiler l’allocation de mémoire et le garbage collection**|-   [Collecte des données de mémoire](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**Profiler le conflit des ressources et l’activité des threads**|-   [Collecte de données de concurrence](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### <a name="sampling-method"></a>Méthode d'échantillonnage  
  
|Tâche|Contenu associé|  
|----------|---------------------|  
|**Profiler des applications autonomes (clientes)**|-   [Collecte de statistiques d’applications en utilisant l’échantillonnage](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|-   **Profiler des services**|-   [Collecte de statistiques d’applications en utilisant l’échantillonnage](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
  
### <a name="analyzing-sampling-data-views-and-reports"></a>Analyse des vues et des rapports de données d’échantillonnage  
 [Vues de données de la méthode d’échantillonnage](../profiling/profiler-sampling-method-data-views.md)