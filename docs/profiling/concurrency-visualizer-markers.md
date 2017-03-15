---
title: "Marqueurs du visualiseur concurrentiel | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.markersui"
ms.assetid: c4692d17-6cd2-4ad1-8590-d7275c771c70
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Marqueurs du visualiseur concurrentiel
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans le Visualiseur concurrentiel, les marqueurs sont des icônes qui représentent des événements dans une application.  En général, l'application génère ces événements pour désigner les phases ou les occurrences dans une application.  Les événements peuvent être générés par l'application ou par des bibliothèques et des runtimes que l'application utilise.  
  
## Types de marqueurs  
 Le Visualiseur concurrentiel utilise trois types de marqueurs pour représenter des événements d'application : balises, messages, et de durées.  
  
1.  Utilisez *une balise* pour indiquer un moment dans le temps intéressant dans votre application.  Par exemple, vous pouvez utiliser un indicateur pour représenter que la valeur d'une variable a atteint un certain seuil ou qu'une exception a été levée.  
  
2.  Un *message* signale également un moment dans le temps, mais vous pouvez l'utiliser pour le traçage de type log.  Par exemple, ce qui auraient pu être déversé dans un fichier journal vous pouvez maintenant l'encapsuler dans un appel de message afin de pouvoir le suivre et l'afficher dans le visualiseur d'accès concurrentiel.  Vous pouvez également utiliser le Visualiseur concurrentiel pour exporter ces données dans un fichier CSV.  
  
3.  Une *étendue* représente un intervalle de temps dans votre application, par exemple, une de ses phases.  
  
## Liaison de marqueurs aux threads  
 Chaque thread qui génère des marqueurs a un canal distinct de chronologie.  L'ID du thread qui est chargé de générer les événements d'un marqueur est affiché à côté de la description du canal de marqueur.  L'ID affiché à gauche du canal de marqueur est égal à l'ID d'un autre thread dans le processus actuel.  
  
## Importance des marqueurs  
 Les marqueurs peuvent avoir un des quatre niveaux d'importance suivants : bas, normal, haut, et critique.  Vous pouvez filtrer les sources des marqueurs selon leurs niveaux d'importances.  Par exemple, si vous souhaitez uniquement afficher des marqueurs d'une source particulière qui a une importance normale ou critique, vous pouvez configurer le filtre dans la boîte de dialogue [paramètres avancés](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md). L'importance d'un marqueur s'affiche dans l'info\-bulle, et dans [Rapport des marqueurs](../profiling/markers-report.md).  
  
## Catégorie de marqueur  
 Une catégorie de marqueur indique un groupe d'événements de marqueur qui proviennent de la même source.  Le Visualiseur concurrentiel utilise des couleurs pour faire la distinction entre différentes catégories des balises et des étendues.  Vous pouvez configurer le Visualiseur concurrentiel pour utiliser des catégories pour filtrer les événements d'un marqueur provenant d'un fournisseur d'événements particulier.  Utilisez la boîte de dialogue [paramètres avancés](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) pour configurer le filtre.  
  
## Sources connues de marqueurs  
 Tout fournisseur ETW peut générer des marqueurs, tant que le fournisseur adhère à certaines contraintes.  Vous pouvez configurer le Visualiseur concurrentiel pour écouter sur des sources d'événements supplémentaires pour les marqueurs.  Par défaut, il écoute les sources d'événements suivantes :  
  
-   [Kit de développement logiciel \(SDK\) du visualiseur concurrentiel](../profiling/concurrency-visualizer-sdk.md)  
  
-   [Task Parallel Library \(TPL\)](../Topic/Task%20Parallel%20Library%20\(TPL\).md)  
  
-   [Flux de données](../Topic/Dataflow%20\(Task%20Parallel%20Library\).md)  
  
-   [Parallel LINQ \(PLINQ\)](../Topic/Parallel%20LINQ%20\(PLINQ\).md)  
  
-   [Concurrency Runtime](/visual-cpp/parallel/concrt/concurrency-runtime)  
  
-   [Scenario Marker Support](http://msdn.microsoft.com/fr-fr/e3b55bc2-b451-4214-ae00-0c7f5a5baec8)  
  
-   [C\+\+ AMP \(C\+\+ Accelerated Massive Parallelism\)](/visual-cpp/parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism)  
  
 Vous pouvez utiliser l'onglet Marqueurs dans la boîte de dialogue [Paramètres avancés](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) pour déterminer si les marqueurs provenant de différentes sources sont affichés dans le Visualiseur concurrentiel, et vous pouvez filtrer les marqueurs selon leur importance et catégorie.  
  
## Marqueurs provenant d'un EventSource  
 Le Visualiseur concurrentiel peut également afficher des événements d'EventSource.  Pour plus d'informations, consultez [Visualisation des événements EventSource en tant que marqueurs](../profiling/visualizing-eventsource-events-as-markers.md).  
  
## Voir aussi  
 [Repérer les marqueurs](../profiling/flag-markers.md)   
 [Marqueurs de messages](../profiling/message-markers.md)   
 [Marqueurs Span](../profiling/span-markers.md)   
 [Visualisation des événements EventSource en tant que marqueurs](../profiling/visualizing-eventsource-events-as-markers.md)