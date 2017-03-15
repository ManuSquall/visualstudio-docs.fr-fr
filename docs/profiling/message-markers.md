---
title: "Marqueurs de messages | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.markers.message"
ms.assetid: 721f40ca-5af2-4a01-b8b6-2b90f6cb7f89
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Marqueurs de messages
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un jeton de message représente la sortie de journal.  Un message est une chaîne qui est émise par un thread spécifique à une heure spécifique.  Vous pouvez exporter des messages dans un fichier texte à utiliser avec d'autres outils.  Vous pouvez placer le pointeur sur un message dans le Visualiseur concurrentiel pour afficher la chaîne de message.  Et vous pouvez afficher les jetons de message dans [Rapport des marqueurs](../profiling/markers-report.md).  L'illustration suivante montre un jeton de message.  
  
## Jetons de regroupement de message  
 Parfois, plusieurs messages se produisent si proche les uns des autres dans le Visualiseur concurrentiel qu'ils ne peuvent pas être dessinés individuellement.  Lorsque cela se produit, un *jeton de regroupement de message* qui représente les messages sous\-jacents est affiché.  Lorsque vous placez le pointeur sur l'une de ces icônes, une info\-bulle affiche le nombre de messages sous\-jacents représentés.  Pour afficher les messages, zoomez. Si vous zoomez complètement et que vous obtenez toujours un marqueur d'agrégation, vous pouvez consulter les messages sous\-jacents dans [Rapport des marqueurs](../profiling/markers-report.md).  
  
## Voir aussi  
 [Marqueurs du visualiseur concurrentiel](../profiling/concurrency-visualizer-markers.md)   
 [Kit de développement logiciel \(SDK\) du visualiseur concurrentiel](../profiling/concurrency-visualizer-sdk.md)