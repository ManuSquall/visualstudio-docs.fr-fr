---
title: Marqueurs d’étendue | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.span
ms.assetid: 736b7765-9c71-44d7-85e5-79787d13d91c
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8f733ccec12e422a11532b8012836422d14d93b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198332"
---
# <a name="span-markers"></a>Marqueurs Span
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un marqueur d’étendue représente une phase significative d’une application. Par exemple, vous pouvez utiliser une étendue pour représenter un intervalle de temps pendant lequel un élément de travail particulier est traité. Sa longueur représente la durée de la phase correspondante de l’application. Cette illustration montre une étendue dans le visualiseur concurrentiel :  
  
 ![Marqueur d’étendue dans le visualiseur concurrentiel](../profiling/media/cvmarkerspan.png "CVMarkerSpan")  
Marqueur d’étendue dans le visualiseur concurrentiel  
  
## <a name="span-category"></a>Catégories d’étendues  
 Un marqueur d’étendue peut être affiché dans cinq couleurs différentes en fonction de sa catégorie. Les couleurs sont répétées quand il y a plus de cinq catégories. La catégorie peut correspondre à n’importe quel entier. Cette illustration présente les cinq couleurs possibles :  
  
 ![Cinq étendues dans différentes catégories](../profiling/media/cvmarkerspancategory.png "CVMarkerSpanCategory")  
Les couleurs des cinq premières catégories d’étendues  
  
## <a name="span-aggregation-markers"></a>Marqueurs d’agrégation d’étendues  
 Parfois, les marqueurs d’étendue sont si proches les uns des autres dans le visualiseur concurrentiel qu’ils ne peuvent pas être dessinés individuellement. Quand c’est le cas, un *marqueur d’agrégation d’étendues* représentant les étendues sous-jacentes est affiché. Quand vous placez le pointeur sur une de ces icônes, une info-bulle montre le nombre d’étendues sous-jacentes qui sont représentées. Pour voir les étendues, faites un zoom avant. Si vous zoomez au maximum et que vous voyez toujours un marqueur d’agrégation d’étendues, vous pouvez voir les marqueurs des étendues sous-jacentes dans le [rapport Marqueurs](../profiling/markers-report.md). Cette illustration montre un marqueur d’agrégation d’étendues :  
  
 ![Un marqueur d’agrégation d’étendues dans le visualiseur concurrentiel](../profiling/media/cvmarkerspanaggregate.png "CVMarkerSpanAggregate")  
Un marqueur d’agrégation d’étendues  
  
## <a name="see-also"></a>Voir aussi  
 [Marqueurs du visualiseur concurrentiel](../profiling/concurrency-visualizer-markers.md)   
 [Kit de développement logiciel (SDK) du visualiseur concurrentiel](../profiling/concurrency-visualizer-sdk.md)
