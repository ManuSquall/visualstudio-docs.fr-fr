---
title: "Collecte de donn&#233;es de temporisation d&#233;taill&#233;es pour une application Web ASP.NET en utilisant la m&#233;thode d&#39;instrumentation du profileur &#224; partir de la ligne de commande | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "instrumentation (méthode de profilage)"
  - "outils de profilage, méthode d'instrumentation"
ms.assetid: 29f2fc55-aaf7-4e18-a672-8815455fba73
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Collecte de donn&#233;es de temporisation d&#233;taill&#233;es pour une application Web ASP.NET en utilisant la m&#233;thode d&#39;instrumentation du profileur &#224; partir de la ligne de commande
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette section décrit les procédures et les options pour collecter des données de performances détaillées pour une application Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] en utilisant l'outil en ligne de commande **VSPerfCmd** et la méthode d'instrumentation.  
  
> [!NOTE]
>  L'outil **VSPerfCmd** vous fournit un accès complet aux fonctionnalités des outils de profilage, telles que l'interruption et la reprise du profilage, ainsi qu'à la collecte de données supplémentaires à partir du processeur et des compteurs de performance Windows.  Vous pouvez également utiliser l'outil en ligne de commande **VSPerfASPNETCmd** lorsque vous n'avez pas besoin de cette fonctionnalité.  Par rapport à l'outil en ligne de commande [VSPerfCmd](../profiling/vsperfcmd.md), aucune variable d'environnement ne doit être définie et le redémarrage de l'ordinateur n'est pas requis.  Pour plus d’informations, consultez [Profilage de site Web rapide avec VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## Tâches courantes  
  
|Tâche|Contenu associé|  
|-----------|---------------------|  
|**Profiler des fichiers binaires compilés statiquement**|-   [Comment : instrumenter une application ASP.NET compilée statiquement et collecter des données de temporisation détaillées](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)|  
|**Profiler des fichiers binaires compilés dynamiquement**|-   [Comment : instrumenter une application ASP.NET compilée dynamiquement et collecter des données de temporisation détaillées](../Topic/How%20to:%20Instrument%20a%20Dynamically%20Compiled%20ASP.NET%20Web%20Application%20and%20Collect%20Detailed%20Timing%20Data%20with%20the%20Profiler%20by%20Using%20the%20Command%20Line.md)|  
  
## Tâches connexes  
  
### Profilage d'applications Web ASP.NET  
  
|Tâche|Contenu associé|  
|-----------|---------------------|  
|**Profiler à l'aide de la méthode d'échantillonnage**|-   [Collecte de statistiques d’applications en utilisant l’échantillonnage](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Profiler l'allocation de mémoire et le garbage collection**|-   [Collecte des données de mémoire](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**Profiler le conflit de ressources et l'activité du thread**|-   [Collecte de données concurrentielles](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### Profilage à l'aide de la méthode d'instrumentation  
  
|Tâche|Contenu associé|  
|-----------|---------------------|  
|**Profiler les applications autonomes \(clientes\)**|-   [Collecte de données de temporisation détaillées à l’aide de l’instrumentation](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Profiler des services**|-   [Collecte de données de temporisation détaillées à l'aide de l'instrumentation](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
  
### Analyse des vues de données et des rapports d'instrumentation  
 [Vues de données de la méthode d'instrumentation](../profiling/instrumentation-method-data-views.md)