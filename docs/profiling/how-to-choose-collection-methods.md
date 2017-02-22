---
title: "Comment&#160;: choisir des m&#233;thodes de collection | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "outils d’analyse des performances, choisir la méthode de collection"
  - "outils de profilage, choisir la méthode de collection"
  - "méthodes de collection de performances"
ms.assetid: c87cfd3a-0fc7-49ae-9c05-d8480891cc63
caps.latest.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 34
---
# Comment&#160;: choisir des m&#233;thodes de collection
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] prennent en charge trois méthodes de collecte des données de performances : l'échantillonnage, l'instrumentation et la concurrence.  Vous pouvez également utiliser la méthode d'échantillonnage ou d'instrumentation pour collecter des données d'allocation de mémoire .NET et de durée de vie.  
  
 **Configuration requise**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Vous pouvez utiliser la propriété **Méthode** de la session de performance pour spécifier la méthode de collecte la plus appropriée pour votre application.  Vous pouvez définir la méthode de collecte à partir de l'Assistant Performance, de l'Explorateur de performances ou des pages des propriétés d'une session de performance.  Si vous utilisez des outils en ligne de commande, consultez [Profilage à partir de la ligne de commande](../profiling/using-the-profiling-tools-from-the-command-line.md) pour plus d'informations.  
  
## Performance \(Assistant\)  
  
#### Pour sélectionner une méthode de collecte à l'aide de l'Assistant Performance  
  
-   Sur la première page de l'Assistant, sélectionnez l'une des options suivantes :  
  
|Option|Description|  
|------------|-----------------|  
|**Échantillonnage de l'UC**|Collecte des statistiques sur l'application utiles pour l'analyse initiale et pour celle des problèmes d'utilisation de l'UC.|  
|**Instrumentation**|Collecte des données de temporisation détaillées utiles pour l'analyse approfondie et pour celle des problèmes de performances d'entrée\/de sortie.|  
|**Allocation de mémoire .NET**|Collecte des données d'allocation de mémoire [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] à l'aide de la méthode de profilage par échantillonnage.|  
|**l'accès concurrentiel ;**|Collecte des données numériques de contention de ressources.|  
  
## Explorateur de performances  
  
#### Pour sélectionner une méthode de collecte à l'aide de l'Explorateur de performances  
  
1.  Dans la barre d'outils de l'**Explorateur de performances**, cliquez sur la flèche en regard de la liste déroulante **Méthode**.  
  
2.  Cliquez sur la méthode de collecte que vous préférez.  
  
## Pages des propriétés de la session de performance  
  
#### Pour sélectionner la méthode d'échantillonnage ou d'instrumentation à l'aide des propriétés de la session de performance  
  
1.  Dans l'**Explorateur de performances**, sélectionnez la session de performance.  
  
     Un nom de fichier de session de performance a une extension .psess.  
  
2.  Cliquez avec le bouton droit sur la session de performance, puis cliquez sur **Propriétés**.  
  
3.  Dans les **Pages de propriétés**, cliquez sur **Général**.  
  
4.  Cliquez sur la méthode de collecte que vous préférez.  
  
    -   Pour plus d'informations sur les autres options disponibles lorsque vous collectez des données d'échantillonnage, consultez [Collecte de statistiques de performance à l’aide de l’échantillonnage](../profiling/collecting-performance-statistics-by-using-sampling.md).  
  
    -   Pour plus d'informations sur les autres options disponibles lorsque vous collectez des données d'échantillonnage, consultez [Collecte de données de temporisation détaillées à l’aide de l’instrumentation](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md).  
  
#### Pour sélectionner une collecte des données de mémoire .NET à l'aide des propriétés de la session de performance  
  
1.  Dans l'**Explorateur de performances**, sélectionnez la session de performance.  
  
     Un nom de fichier de session de performance a une extension .psess.  
  
2.  Cliquez avec le bouton droit sur la session de performance, puis cliquez sur **Propriétés**.  
  
3.  Dans les **Pages de propriétés**, cliquez sur **Général**.  
  
4.  Cliquez sur **Échantillonnage** ou sur **Instrumentation**.  
  
5.  Cliquez sur **Collecter les informations d'allocation d'objets .NET** pour collecter la taille et le nombre d'allocations d'objets [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
6.  \(Facultatif\) Cliquez sur **Collecter aussi les informations de durée de vie des objets .NET** pour collecter des informations sur les générations de garbage collection dans lesquelles la mémoire d'objets a été récupérée.  
  
     Pour plus d'informations sur les autres options disponibles lorsque vous collectez des données de mémoire .NET, consultez [Collecte de données liées à l’allocation et à la durée de vie de la mémoire .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md).  
  
#### Pour sélectionner une collecte des données de concurrence à l'aide des propriétés de la session de performance  
  
1.  Dans l'**Explorateur de performances**, cliquez avec le bouton droit sur la session de performance, puis cliquez sur **Propriétés**.  
  
2.  Dans les **Pages de propriétés**, cliquez sur **Général**.  
  
3.  Cliquez sur **Concurrence**.  
  
## Voir aussi  
 [Configuration de sessions de performance](../profiling/configuring-performance-sessions.md)   
 [Fonctionnement des valeurs de données d’échantillonnage](../profiling/understanding-sampling-data-values.md)   
 [Propriétés d’une session de performance](../profiling/performance-session-properties.md)