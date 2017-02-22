---
title: "Proc&#233;dure&#160;: collecter les donn&#233;es des compteurs UC &#224; l’aide de la m&#233;thode d’instrumentation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.cpucounters"
helpviewer_keywords: 
  - "outils de profilage, utiliser des compteurs UC portables"
  - "outils d’analyse des performances, compteurs UC portables"
ms.assetid: 102fb6ca-5fbf-4b05-925f-56912ce3f44b
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# Proc&#233;dure&#160;: collecter les donn&#233;es des compteurs UC &#224; l’aide de la m&#233;thode d’instrumentation
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un compteur d'événements UC sert à collecter les données de performance sur le matériel.  Cette rubrique vous indique comment collecter des données de compteur d'événements lorsque vous utilisez la méthode de profilage par instrumentation.  
  
 **Configuration requise**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Deux types d'événements de compteur UC se produisent :  
  
-   Événements portables : événements UC pouvant être collectés quelle que soit l'UC spécifique.  
  
-   Événements de plateforme : événements UC associés à une UC spécifique.  
  
 Les événements portables incluent les événements généraux, comme les instructions retirées et les cycles non interrompus, les événements de mémoire tampon UC, les événements de branche et les événements du cache L2.  Les compteurs d'événements de plateforme disponibles sont déterminés par le fabricant du processeur.  
  
 Les catégories d'événements peuvent être partagées entre les compteurs d'événements portables et de plateforme.  Par exemple, les catégories de données suivantes sont souvent communes aux deux types :  
  
-   Événements de la mémoire :  
  
-   Événements frontaux.  
  
-   Événements de branche.  
  
 Vous pouvez recueillir les données des compteurs de performance de deux manières différentes dans le profileur :  
  
-   Collectez les données issues d'un ou plusieurs compteurs lors du profilage par instrumentation.  
  
-   Spécifiez un événement de compteur en tant qu'intervalle d'échantillonnage lors du profilage par échantillonnage.  Pour plus d’informations, consultez [Comment : choisir des événements d’échantillonnage](../Topic/How%20to:%20Choose%20Sampling%20Events.md).  
  
### Pour collecter les données des compteurs de performance de l'UC lors du profilage par instrumentation  
  
1.  Dans les **Pages de propriétés** de la session de performance, cliquez sur **Compteurs UC.**  
  
2.  Activez la case à cocher **Collecter les compteurs UC**.  
  
3.  Développez l'arborescence **Compteurs de performance disponibles** jusqu'à ce que vous trouviez les exemples d'événements à collecter.  
  
4.  Pour chaque événement à collecter, sélectionnez l'événement, puis cliquez sur le bouton fléché droit pour l'ajouter à la liste **Compteurs sélectionnés**.  
  
    > [!NOTE]
    >  L'option **Compteurs de performance disponibles** est activée uniquement si vous activez la case à cocher **Collecter les compteurs UC**.  
  
## Voir aussi  
 [Configuration de sessions de performance](../profiling/configuring-performance-sessions.md)   
 [Propriétés d’une session de performance](../profiling/performance-session-properties.md)   
 [Compteurs UC et Windows](../profiling/cpu-and-windows-counters.md)   
 [Comment : choisir des événements d’échantillonnage](../Topic/How%20to:%20Choose%20Sampling%20Events.md)