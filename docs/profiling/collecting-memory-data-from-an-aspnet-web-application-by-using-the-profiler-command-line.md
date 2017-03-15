---
title: "Collecte des donn&#233;es de m&#233;moire d&#39;une application Web ASP.NET en utilisant la ligne de commande du profileur | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "profilage de la mémoire .NET (méthode)"
  - "outils de profilage, mémoire .NET (méthode)"
ms.assetid: 57acf2b0-327a-4c0e-8078-ac2f6d99457d
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Collecte des donn&#233;es de m&#233;moire d&#39;une application Web ASP.NET en utilisant la ligne de commande du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette section décrit les procédures et options pour collecter des données d'allocation de mémoire et de durée de vie des objets pour une application Web ASP.NET à l'aide de l'outil en ligne de commande **VSPerfCmd**.  
  
> [!NOTE]
>  L'outil **VSPerfCmd** vous fournit un accès complet aux fonctionnalités des outils de profilage, telles que l'interruption et la reprise du profilage, ainsi qu'à la collecte de données supplémentaires à partir du processeur et des compteurs de performance Windows.  Vous pouvez également utiliser l'outil en ligne de commande **VSPerfASPNETCmd** lorsque vous n'avez pas besoin de ces fonctionnalités.  Par rapport à l'outil en ligne de commande [VSPerfCmd](../profiling/vsperfcmd.md), aucune variable d'environnement ne doit être définie et le redémarrage de l'ordinateur n'est pas requis.  Pour plus d’informations, consultez [Profilage de site Web rapide avec VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## Tâches courantes  
  
|Tâche|Contenu associé|  
|-----------|---------------------|  
|**Attacher le profileur à une application ASP.NET en cours d'exécution**|-   [Comment : attacher le profileur à une application Web ASP.NET pour collecter des données de mémoire](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|  
|**Instrumenter des fichiers binaires statiquement compilés**|-   [Comment : instrumenter une application ASP.NET compilée statiquement et collecter des données de mémoire](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
|**Instrumenter des fichiers binaires dynamiquement compilés**|-   [Comment : instrumenter une application ASP.NET compilée dynamiquement et collecter des données de mémoire](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
## Tâches connexes  
  
### Profilage d'applications Web ASP.NET  
  
|Tâche|Contenu associé|  
|-----------|---------------------|  
|**Profiler à l'aide de la méthode d'échantillonnage**|-   [Collecte de statistiques d’applications en utilisant l’échantillonnage](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Profiler à l'aide de la méthode d'instrumentation**|-   [Collecte de données de temporisation détaillées à l'aide de l'instrumentation](../profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line.md)|  
|**Profiler le conflit de ressources et l'activité du thread**|-   [Collecte de données concurrentielles](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### Profilage des données de mémoire .NET Framework  
  
|Tâche|Contenu associé|  
|-----------|---------------------|  
|**Profiler les applications autonomes \(clientes\)**|-   [Collecte de données de mémoire .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Profiler des services**|-   [Collecte de données de mémoire .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
  
### Analyse des vues de données et des rapports de mémoire .NET  
 [Vues de données de mémoire .NET](../profiling/dotnet-memory-data-views.md)  
  
## Référence  
 [Référence d'outils de profilage de ligne de commande](../profiling/command-line-profiling-tools-reference.md)