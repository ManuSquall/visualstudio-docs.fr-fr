---
title: "Marqueurs Span | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.markers.span"
ms.assetid: 736b7765-9c71-44d7-85e5-79787d13d91c
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Marqueurs Span
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un jeton d'étendue représente une phase explicite d'une application.  Par exemple, vous pouvez utiliser une étendue pour représenter un intervalle de temps pendant lequel un élément de travail particulier est traité.  Sa longueur représente la durée de la phase correspondante de l'application.  Cette illustration affiche une étendue dans le visualiseur concurrentiel :  
  
 ![Marqueur d’étendue du visualiseur concurrentiel](../profiling/media/cvmarkerspan.png "CVMarkerSpan")  
Un marqueur d'étendue dans le visualiseur concurrentiel  
  
## Catégorie d'étendue  
 Un jeton d'étendue est affichée de cinq couleurs différentes, selon sa catégorie.  Les couleurs sont répétées s'il y a plus de cinq catégories.  La catégorie peut être n'importe quel entier.  Cette illustration représente les cinq couleurs possibles :  
  
 ![Cinq étendues de différentes catégories](../profiling/media/cvmarkerspancategory.png "CVMarkerSpanCategory")  
Les couleurs des cinq premières catégories d'étendues  
  
## Marques de regroupement d'étendues  
 Parfois des marques d'étendue se produisent si proche les une des autres dans le visualiseur concurrentiel qu'elles ne peuvent pas être dessinées individuellement.  Lorsque cela se produit, un *jeton de regroupement d'étendue* gris qui représente les étendues sous\-jacent est affiché.  Lorsque vous placez le pointeur sur l'une de ces icônes, une info\-bulle affiche le nombre d'étendues sous\-jacentes représentées.  Pour afficher les étendues, zoomez en avant.  Si vous effectuez un zoom avant et que vous obtenez un jeton de regroupement d'étendue, vous pouvez afficher les étendues sous\-jacentes dans [Rapport des marqueurs](../profiling/markers-report.md).  Cette illustration représente un jeton de regroupement d'étendues :  
  
 ![Marqueur d'étendue d'agrégation du visualiseur concurrentiel](../profiling/media/cvmarkerspanaggregate.png "CVMarkerSpanAggregate")  
Un jeton de regroupement d'étendues  
  
## Voir aussi  
 [Marqueurs du visualiseur concurrentiel](../profiling/concurrency-visualizer-markers.md)   
 [Kit de développement logiciel \(SDK\) du visualiseur concurrentiel](../profiling/concurrency-visualizer-sdk.md)