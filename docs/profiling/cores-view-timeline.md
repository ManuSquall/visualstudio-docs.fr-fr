---
title: Chronologie de la vue Cœurs | Microsoft Docs
description: 'Découvrez les principes de base de la chronologie : comment déterminer le thread qui a été exécuté sur quel cœur à un moment donné, et comment effectuer un zoom avant ou arrière.'
custom.ms: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cores.timeline.threads
helpviewer_keywords:
- Concurrency Visualizer, Cores View Timeline
ms.assetid: 10f0c666-ac2f-4ac5-9fb5-a88f660ab840
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: de09394bfc071cbe3dd1fedad52d1e5a511b62c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882893"
---
# <a name="cores-view-timeline"></a>Chronologie de la vue Cœurs
Chaque ligne de la chronologie représente un cœur de processeur logique sur le système profilé. Pour chaque ligne, l’axe horizontal indique le thread qui s’exécutait sur un cœur logique à un moment donné dans le temps. Vous pouvez pointer sur une couleur dans une chronologie pour afficher une info-bulle qui identifie le thread. Pour faciliter l’identification du thread, la légende dans le bas de la fenêtre indique ce que représente chaque couleur. Utilisez l’outil Zoom pour effectuer un zoom avant ou arrière, en cliquant et en faisant glisser, ou en appuyant sur Ctrl et en actionnant la roulette de la souris. La cohérence du zoom est conservée quand vous basculez entre la vue Cœurs et la vue Threads.

## <a name="see-also"></a>Voir aussi
- [Affichage Cœurs](../profiling/cores-view.md)
- [Contrôle zoom (vue threads)](../profiling/zoom-control-threads-view.md)