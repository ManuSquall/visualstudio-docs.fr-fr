---
title: Marqueurs d’étendue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.span
ms.assetid: 736b7765-9c71-44d7-85e5-79787d13d91c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c69b48a5b1b551e2e29b9aa10e7f68ff0df0e379
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62980961"
---
# <a name="span-markers"></a>Marqueurs d’étendue
Un marqueur d’étendue représente une phase significative d’une application. Par exemple, vous pouvez utiliser une étendue pour représenter un intervalle de temps pendant lequel un élément de travail particulier est traité. Sa longueur représente la durée de la phase correspondante de l’application. Cette illustration montre une étendue dans le visualiseur concurrentiel :

 ![Marqueur d’étendue dans le visualiseur concurrentiel](../profiling/media/cvmarkerspan.png "CVMarkerSpan") Marqueur d’étendue dans le visualiseur concurrentiel

## <a name="span-category"></a>Catégories d’étendues
 Un marqueur d’étendue peut être affiché dans cinq couleurs différentes en fonction de sa catégorie. Les couleurs sont répétées quand il y a plus de cinq catégories. La catégorie peut correspondre à n’importe quel entier. Cette illustration présente les cinq couleurs possibles :

 ![Cinq étendues dans différentes catégories](../profiling/media/cvmarkerspancategory.png "CVMarkerSpanCategory") Couleurs des cinq premières catégories

## <a name="span-aggregation-markers"></a>Marqueurs d’agrégation d’étendues
 Parfois, les marqueurs d’étendue sont si proches les uns des autres dans le visualiseur concurrentiel qu’ils ne peuvent pas être dessinés individuellement. Quand c’est le cas, un *marqueur d’agrégation d’étendues* représentant les étendues sous-jacentes est affiché. Quand vous placez le pointeur sur une de ces icônes, une info-bulle montre le nombre d’étendues sous-jacentes qui sont représentées. Pour voir les étendues, faites un zoom avant. Si vous zoomez au maximum et que vous voyez toujours un marqueur d’agrégation d’étendues, vous pouvez voir les marqueurs des étendues sous-jacentes dans le [rapport Marqueurs](../profiling/markers-report.md). Cette illustration montre un marqueur d’agrégation d’étendues :

 ![Marqueur d’agrégation d’étendues dans le visualiseur concurrentiel](../profiling/media/cvmarkerspanaggregate.png "CVMarkerSpanAggregate") Marqueur d’agrégation d’étendues

## <a name="see-also"></a>Voir aussi
- [Marqueurs du visualiseur concurrentiel](../profiling/concurrency-visualizer-markers.md)
- [Kit SDK du visualiseur concurrentiel](../profiling/concurrency-visualizer-sdk.md)