---
title: Marqueurs de messages | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.markers.message
ms.assetid: 721f40ca-5af2-4a01-b8b6-2b90f6cb7f89
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd2487466518622ebd1b2a52c4e4697be23a40d9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47500987"
---
# <a name="message-markers"></a>Marqueurs de messages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [marqueurs de messages](https://docs.microsoft.com/visualstudio/profiling/message-markers).  
  
Un jeton de message représente une sortie de journal. Un message est une chaîne émise par un thread spécifique à un moment donné. Vous pouvez exporter des messages vers un fichier texte en vue de les utiliser avec d’autres outils. Vous pouvez placer le pointeur sur un message dans le visualiseur concurrentiel pour afficher la chaîne du message. Vous pouvez aussi afficher tous les marqueurs de message dans le [rapport Marqueurs](../profiling/markers-report.md).  L’illustration suivante présente un marqueur de message.  
  
## <a name="message-aggregation-markers"></a>Marqueurs d’agrégation de messages  
 Parfois, les messages sont générés de manière si rapprochée dans le visualiseur concurrentiel qu’ils ne peuvent pas être affichés individuellement. Quand cela se produit, un *marqueur d’agrégation de messages* représentant les messages sous-jacents s’affiche. Quand vous placez le pointeur sur l’une de ces icônes, une info-bulle affiche le nombre de messages sous-jacents représentés. Pour afficher les messages, faites un zoom avant.  Si vous zoomez au maximum et obtenez toujours un marqueur d’agrégation, vous pouvez afficher les messages sous-jacents dans le [rapport Marqueurs](../profiling/markers-report.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Marqueurs du visualiseur concurrentiel](../profiling/concurrency-visualizer-markers.md)   
 [Kit SDK du visualiseur concurrentiel](../profiling/concurrency-visualizer-sdk.md)



