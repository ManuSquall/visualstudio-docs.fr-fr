---
title: Marqueurs de messages | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.message
ms.assetid: 721f40ca-5af2-4a01-b8b6-2b90f6cb7f89
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b668f0331345e6a1022ef79105614f4a22e91d9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62830076"
---
# <a name="message-markers"></a>Marqueurs de messages
Un jeton de message représente une sortie de journal. Un message est une chaîne émise par un thread spécifique à un moment donné. Vous pouvez exporter des messages vers un fichier texte en vue de les utiliser avec d’autres outils. Vous pouvez placer le pointeur sur un message dans le visualiseur concurrentiel pour afficher la chaîne du message. Vous pouvez aussi afficher tous les marqueurs de message dans le [rapport Marqueurs](../profiling/markers-report.md).  L’illustration suivante présente un marqueur de message.

## <a name="message-aggregation-markers"></a>Marqueurs d’agrégation de messages
 Parfois, les messages sont générés de manière si rapprochée dans le visualiseur concurrentiel qu’ils ne peuvent pas être affichés individuellement. Quand cela se produit, un *marqueur d’agrégation de messages* représentant les messages sous-jacents s’affiche. Quand vous placez le pointeur sur l’une de ces icônes, une info-bulle affiche le nombre de messages sous-jacents représentés. Pour afficher les messages, faites un zoom avant.  Si vous zoomez au maximum et obtenez toujours un marqueur d’agrégation, vous pouvez afficher les messages sous-jacents dans le [rapport Marqueurs](../profiling/markers-report.md).

## <a name="see-also"></a>Voir aussi
- [Marqueurs du visualiseur concurrentiel](../profiling/concurrency-visualizer-markers.md)
- [Kit SDK du visualiseur concurrentiel](../profiling/concurrency-visualizer-sdk.md)