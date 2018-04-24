---
title: Graphique d’activité GPU | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 41b7812db05b61c351346e5f0dcfa1bf4bd7bd1f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="gpu-activity-graph"></a>Graphique d'activité GPU
Le graphique d’activité GPU du visualiseur concurrentiel affiche le niveau d’activité DirectX du système. Cette activité se mesure par le nombre de moteurs DirectX qui sont utilisés dans le temps.  Le graphique n’affiche cependant pas quels moteurs sont utilisés.  Un moteur est considéré comme utilisé lorsqu’il traite un travail GPU.  
  
## <a name="gpu-activity-graph-colors"></a>Couleurs du graphique d’activité GPU  
 Le vert indique la consommation des moteurs DirectX par le processus en cours.  
  
 Le gris clair indique l’utilisation des moteurs DirectX par d’autres processus sur le système. Pour réduire la consommation des moteurs DirectX par d’autres processus, réduisez le nombre des processus qui s’exécutent sur le système.  
  
 Le blanc indique la disponibilité des moteurs DirectX inutilisés sur le système. Ces moteurs sont disponibles pour votre processus si vous leur trouvez d’autres usages. Certains moteurs ne peuvent être utilisés que pour certains types de tâches.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue Utilisation](../profiling/utilization-view.md)