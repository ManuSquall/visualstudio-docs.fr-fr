---
title: "Configuration de sessions de performance pour les outils de profilage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tâches courantes, performances"
  - "tâches courantes, outils de profilage"
  - "outils de profilage, tâches courantes"
  - "performances, collecter des données"
ms.assetid: e1c3ba41-ffca-4edf-9a7f-8a5a9244ef9b
caps.latest.revision: 36
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 36
---
# Configuration de sessions de performance pour les outils de profilage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Grâce aux outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous pouvez collecter une grande diversité de données de performances pour de nombreux types d'applications différents.  Cette section vous indique comment utiliser l'Assistant Performanceet les propriétés de la session de performance et du fichier binaire cible pour configurer les outils de profilage afin de collecter les données qui vous intéressent.  Les propriétés de configuration des outils de profilage peuvent également servir à contrôler le volume de données recueillies lors de l'exécution du profilage.  Pour plus d’informations, consultez [Contrôle de la collecte de données](../profiling/controlling-data-collection.md).  
  
> [!NOTE]
>  Dans de nombreux cas, l'utilisation des propriétés par défaut de l'Assistant Performance est efficace pour collecter les données de profilage.  Pour plus d'informations, consultez [Guide du débutant en profilage des performances](../profiling/beginners-guide-to-performance-profiling.md) et [Prise en main](../profiling/getting-started-with-performance-tools.md).  
  
## Tâches courantes  
  
|Tâche|Contenu associé|  
|-----------|---------------------|  
|**Définir les options de profilage de base :** vous devez configurer [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] pour utiliser le serveur de symboles de Microsoft.  Vous êtes ainsi assuré d'avoir accès aux symboles \(par exemple, les noms de fonction et de paramètre\) pour la version actuelle de Windows et d'autres applications Microsoft.  Vous pouvez également spécifier d'autres options générales \(par exemple, les autorisations du système sur les outils de profilage et les noms des fichiers de données de profilage\) avant le démarrage d'une session de profilage.|-   [Comment : référencer les informations de symboles Windows](../profiling/how-to-reference-windows-symbol-information.md)<br />-   [Procédure : sérialiser les informations de symboles](../profiling/how-to-serialize-symbol-information.md)<br />-   [Comment : définir la session de profilage actuelle](../Topic/How%20to:%20Set%20the%20Current%20Session.md)<br />-   [Comment : définir des autorisations de profilage](../profiling/how-to-set-permissions.md)<br />-   [Comment : définir les options de nom de fichier de données de profilage](../profiling/how-to-set-performance-data-file-name-options.md)|  
|**Spécifier les données que vous souhaitez collecter :** les procédures que vous utilisez pour configurer une session de profilage dépendent du type d'application cible que vous souhaitez profiler et du type de données de performance que vous souhaitez collecter.|-   [Comment : choisir des méthodes de collection](../profiling/how-to-choose-collection-methods.md)<br />-   [Collecte de statistiques de performance à l’aide de l’échantillonnage](../profiling/collecting-performance-statistics-by-using-sampling.md)<br />-   [Collecte de données liées à l’allocation et à la durée de vie de la mémoire .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Collecte de données de temporisation détaillées à l’aide de l’instrumentation](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)<br />-   [Comment : profiler du code JavaScript \(ECMA\) dans des pages web](../Topic/How%20to:%20Profile%20JavaScript%20Code%20in%20Web%20Pages.md)<br />-   [Collecte de données de concurrence de threads et de processus](../profiling/collecting-thread-and-process-concurrency-data.md)<br />-   [Collecte de données de performance supplémentaires](../profiling/collecting-additional-performance-data.md)|  
|**Définir des options de configuration avancées :** lorsque vous profilez des applications .NET Framework qui chargent plusieurs versions du Common Language Run\-time \(CLR\), vous pouvez spécifier la version à profiler.  Lorsque vous disposez de plusieurs fichiers .exe dans une session de performance, vous pouvez définir l'ordre de démarrage des binaires.|-   [Comment : spécifier le runtime .NET Framework à profiler dans les scénarios côte à côte](../Topic/How%20to:%20Specify%20the%20.NET%20Framework%20Runtime.md)<br />-   [Comment : spécifier le binaire à démarrer](../profiling/how-to-specify-the-binary-to-start.md)|  
  
## Rubriques connexes  
 [Contrôle de la collecte de données](../profiling/controlling-data-collection.md)  
  
## Voir aussi  
 [Utilisation des outils de profilage](../profiling/performance-explorer.md)