---
title: Marqueurs indicateurs | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.markers.flag
ms.assetid: f3ec919e-63e5-484b-adbf-8f0e79342e75
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 79105e43cba14c12cf0f82edd05b57286c012ee5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="flag-markers"></a>Repérer les marqueurs
Un marqueur indicateur représente un événement qui s’est produit à un instant donné dans une application. Un indicateur peut représenter de nombreux types d’événements d’application. Par exemple, un indicateur peut apparaître lorsqu’un élément de travail a été planifié ou lorsqu’une exception a été levée. Les runtimes, tels que la bibliothèque parallèle de tâches, peuvent également générer des indicateurs.  
  
## <a name="flag-importance"></a>Importance des indicateurs  
 La taille des indicateurs dépend de leur importance. Comme pour tout autre type de marqueur, leur niveau d’importance peut être bas, normal, élevé ou critique.  Cette illustration montre l’apparence des marqueurs selon leur niveau d’importance :  
  
 ![Marqueurs d’importance Basse, Normale, Élevée et Critique](../profiling/media/cvmarkerimportance.png "CVMarkerImportance")  
Marqueurs indiquant l’importance des indicateurs  
  
## <a name="flag-category"></a>Catégories des indicateurs  
 Les indicateurs sont de cinq couleurs différentes, selon leur catégorie. Les couleurs sont réutilisées lorsqu’il y a plus de cinq catégories. Vous ne pouvez pas choisir la couleur. Comme pour tout autre marqueur, la catégorie peut correspondre à n’importe quel entier. L’illustration suivante montre les couleurs des cinq premières catégories.  
  
 ![Les cinq couleurs des marqueurs de catégorie](../profiling/media/cvmarkercategory.png "CVMarkerCategory")  
Marqueurs montrant les catégories  
  
## <a name="alerts"></a>Alertes  
 Une alerte est un indicateur rouge qui représente un événement d’application critique, tel qu’une exception.  Voici un exemple d’alerte :  
  
 ![Marqueur d’alerte du visualiseur concurrentiel](../profiling/media/cvmarkeralert.png "CVMarkerAlert")  
Marqueur d’alerte  
  
## <a name="aggregation-flags"></a>Indicateurs d’agrégation  
 Parfois, les indicateurs sont générés de manière si rapprochée dans le visualiseur concurrentiel qu’ils ne peuvent pas être affichés individuellement. Lorsque cela se produit, un *indicateur d’agrégation* de couleur grise s’affiche pour représenter les indicateurs sous-jacents. Lorsque vous placez le pointeur sur l’une de ces icônes, une info-bulle affiche le nombre d’indicateurs sous-jacents qui sont représentés. Pour afficher les indicateurs, faites un zoom avant. Si vous zoomez au maximum et obtenez toujours un indicateur d’agrégation, vous pouvez afficher les indicateurs sous-jacents dans le [rapport Marqueurs](../profiling/markers-report.md).  
  
 Les indicateurs d’agrégation peuvent avoir différentes tailles. La taille varie selon le niveau d’importance de l’indicateur le plus important de l’agrégation. L’illustration suivante montre les indicateurs d’agrégation, par ordre croissant d’importance.  
  
 ![Indicateurs d’agrégation montrant quatre niveaux d’importance](../profiling/media/cvmarkeraggregate.png "CVMarkerAggregate")  
Indicateurs d’agrégation par niveau d’importance  
  
## <a name="see-also"></a>Voir aussi  
 [Marqueurs du visualiseur concurrentiel](../profiling/concurrency-visualizer-markers.md)   
 [Kit SDK du visualiseur concurrentiel](../profiling/concurrency-visualizer-sdk.md)