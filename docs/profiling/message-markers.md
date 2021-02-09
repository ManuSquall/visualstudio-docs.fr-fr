---
title: Marqueurs de messages | Microsoft Docs
description: Découvrez comment vous pouvez exporter des messages dans un fichier texte pour les utiliser avec d’autres outils et placer le pointeur sur un message dans le visualiseur concurrentiel pour afficher la chaîne de message.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.message
ms.assetid: 721f40ca-5af2-4a01-b8b6-2b90f6cb7f89
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d0ce91a47bb2158f3cf684e1634a684f372a044d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879941"
---
# <a name="message-markers"></a>Marqueurs de messages
Un jeton de message représente une sortie de journal. Un message est une chaîne émise par un thread spécifique à un moment donné. Vous pouvez exporter des messages vers un fichier texte en vue de les utiliser avec d’autres outils. Vous pouvez placer le pointeur sur un message dans le visualiseur concurrentiel pour afficher la chaîne du message. Vous pouvez afficher tous les marqueurs de messages dans le [rapport marqueurs](../profiling/markers-report.md).  L’illustration suivante présente un marqueur de message.

## <a name="message-aggregation-markers"></a>Marqueurs d’agrégation de messages
 Parfois, les messages sont générés de manière si rapprochée dans le visualiseur concurrentiel qu’ils ne peuvent pas être affichés individuellement. Quand cela se produit, un *marqueur d’agrégation de messages* représentant les messages sous-jacents s’affiche. Quand vous placez le pointeur sur l’une de ces icônes, une info-bulle affiche le nombre de messages sous-jacents représentés. Pour afficher les messages, faites un zoom avant.  Si vous zoomez au maximum et obtenez toujours un marqueur d’agrégation, vous pouvez afficher les messages sous-jacents dans le [rapport Marqueurs](../profiling/markers-report.md).

## <a name="see-also"></a>Voir aussi
- [Marqueurs du visualiseur concurrentiel](../profiling/concurrency-visualizer-markers.md)
- [Kit de développement logiciel (SDK) du visualiseur concurrentiel](../profiling/concurrency-visualizer-sdk.md)