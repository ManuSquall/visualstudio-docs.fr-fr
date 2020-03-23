---
title: Vue Cœurs | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.cores
helpviewer_keywords:
- Concurrency Visualizer, Cores View
ms.assetid: e47af672-9785-4899-bd45-4d9dda3c396f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99b26b913a42a563e0226ff2697b947684dfec53
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62553056"
---
# <a name="cores-view"></a>Vue Cœurs
**L’Affichage cœurs** indique la façon dont l’exécution du thread a été mappée aux cœurs de processeurs logiques (choisissez **Analyser** > **Visualiseur concurrentiel** pour démarrer le visualiseur concurrentiel). Si vous écrivez des applications serveur, cette vue peut vous aider à optimiser les performances du cache à l’aide de la gestion du pool de thread ou de l’affinité de thread. Elle peut également vous aider à examiner les cas où l’utilisation de l’affinité de thread peut avoir aggravé le problème de migration inter-cœurs. La vue Cœurs comporte deux parties : un graphique et une légende.

 Dans le graphique, les cœurs logiques sont représentés sur l’axe des ordonnées et le temps sur l’axe des abscisses. Chaque thread du graphique a une couleur propre pour que vous puissiez suivre ses mouvements d’un cœur à l’autre dans le temps. Vous pouvez filtrer les threads du graphique en les sélectionnant dans la zone de légende.

 La zone de légende comporte une entrée pour chaque couleur du graphique. Chaque entrée indique la couleur et le nom du thread, le nombre de changements de contexte inter-cœurs, le nombre total de changements de contexte et le pourcentage de changements de contexte inter-cœurs. Les lignes de la légende sont triées selon le nombre de changements de contexte inter-cœurs, dans l’ordre décroissant. La légende répertorie uniquement les threads exécutés pendant l’intervalle de temps affiché.  La liste est mise à jour quand vous effectuez un zoom ou un panoramique.

## <a name="see-also"></a>Voir aussi
- [Visualiseur concurrentiel](../profiling/concurrency-visualizer.md)
- [vue Utilisation](../profiling/utilization-view.md)
- [Vue Threads](../profiling/threads-view-parallel-performance.md)