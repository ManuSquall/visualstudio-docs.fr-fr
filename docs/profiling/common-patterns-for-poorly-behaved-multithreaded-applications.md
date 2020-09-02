---
title: Modèles courants pour des applications multithread au comportement médiocre | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.tools.gallery
helpviewer_keywords:
- Concurrency Visualizer, common patterns for poorly-behaved multithreaded applications
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4aec033266ccb2a6e6dcd0342669b7c31082488a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62788903"
---
# <a name="common-patterns-for-poorly-behaved-multithreaded-applications"></a>Modèles courants pour des applications multithread au comportement médiocre

Le visualiseur concurrentiel permet aux développeurs de visualiser le comportement d’une application multithread. Cet outil comprend une galerie de modèles courants pour les applications multithread au comportement médiocre. La galerie comprend des modèles visuels typiques et reconnaissables, exposés via l’outil, ainsi qu’une explication du comportement représenté par chaque modèle, le résultat probable de ce comportement et l’approche la plus courante pour le résoudre.

## <a name="lock-contention-and-serialized-execution"></a>Conflits de verrous et exécution sérialisée

![Contention de verrouillage entraînant une exécution sérialisée](../profiling/media/lockcontention_serialized.png "LockContention_Serialized")

Parfois, une application parallélisée continue de s’exécuter de façon sérialisée alors qu’elle dispose de plusieurs threads et que l’ordinateur contient un nombre suffisant de cœurs logiques. Le premier symptôme que vous observerez sont de mauvaises performances multithread, peut-être même un peu plus lentes qu’une implémentation en série. Dans la vue Threads, vous ne voyez pas plusieurs threads s’exécuter en parallèle, mais un seul thread qui s’exécute en continu. À ce stade, si vous cliquez sur un segment de synchronisation d’un thread, vous voyez la pile des appels du thread bloqué (pile des appels de blocage) et le thread qui a supprimé la condition de blocage (pile des appels de déblocage). En outre, si la pile des appels de déblocage se produit au cours du processus que vous analysez, un connecteur de thread s’affiche. À ce stade, vous pouvez naviguer dans votre code à partir des piles d’appels de blocage et de déblocage pour connaître plus précisément la cause de la sérialisation.

Comme le montre l’illustration suivante, le visualiseur concurrentiel peut également exposer ce symptôme dans la vue Utilisation de l’UC, où vous voyez que, malgré la présence de plusieurs threads, l’application n’utilise qu’un seul cœur logique.

Pour plus d’informations, consultez la section « Démarrer avec le problème » dans l’article de MSDN Magazine [Performances des threads - Profilage de simultanéité des contentions de ressources dans Visual Studio 2010](https://msdn.microsoft.com/magazine/ff714587.aspx).

![Contention de verrouillage](../profiling/media/lockcontention_2.png "LockContention_2")

## <a name="uneven-workload-distribution"></a>Distribution inégale de la charge de travail

![Charge de travail inégale](../profiling/media/unevenworkload_1.png "UnevenWorkLoad_1")

Lorsque la charge de travail est mal répartie entre les différents threads parallèles d’une application, un modèle typique en escalier apparaît chaque fois qu’un thread termine son travail, comme le montre l’illustration précédente. Le visualiseur concurrentiel présente souvent des heures de début très proches pour chaque thread simultané. Cependant, ces threads ne se terminent pas simultanément comme prévu. Ce modèle indique une distribution inégale de la charge de travail entre les différents threads parallèles, ce qui peut entraîner une baisse des performances. Pour ce type de problème, la meilleure approche consiste à réévaluer l’algorithme selon lequel la charge de travail est répartie entre les threads parallèles.

Comme le montre l’illustration suivante, le visualiseur concurrentiel peut également exposer ce symptôme dans la vue Utilisation de l’UC sous la forme d’une baisse progressive de l’utilisation du processeur.

![Charge de travail inégale](../profiling/media/unevenworkload_2.png "UnevenWorkload_2")

## <a name="oversubscription"></a>Surabonnement

![Surabonnement](../profiling/media/oversubscription.png "Surabonnement")

Dans le cas d’un surabonnement, le nombre de threads actifs d’un processus est supérieur au nombre de cœurs logiques disponibles sur le système. L’illustration précédente montre les résultats d’un surabonnement, avec une importante anticipation de tous les threads actifs. De plus, la légende montre qu’un pourcentage important du temps est consacré à l’anticipation (84 % dans cet exemple). Cela peut indiquer que le processus demande au système d’exécuter plus de threads simultanés qu’il n’existe de cœurs logiques. Toutefois, cela peut également indiquer que d’autres processus présents sur le système utilisent des ressources censées être disponibles pour ce processus.

Vous devez tenir compte de ce qui suit lorsque vous examinez ce problème :

- L’ensemble du système peut être en surabonnement. Envisagez l’éventualité que d’autres processus présents sur le système puissent anticiper vos threads. Lorsque vous placez le pointeur de la souris sur un segment d’anticipation de la vue Threads, une info-bulle identifie le thread, ainsi que le processus qui a anticipé le thread. Ce processus n’est pas nécessairement celui qui s’est exécuté durant toute l’anticipation de votre processus. Cependant, il fournit une bonne indication de ce qui est à l’origine de la pression d’anticipation exercée sur votre processus.

- Évaluez la façon dont votre processus détermine le nombre de threads nécessaires à l’exécution lors de cette phase de travail. Si votre processus calcule directement le nombre de threads parallèles actifs, modifiez cet algorithme pour une meilleure prise en compte du nombre de cœurs logiques disponibles sur le système. Si vous utilisez le runtime d’accès concurrentiel, la bibliothèque parallèle de tâches ou PLINQ, ce sont ces bibliothèques qui se chargeront du calcul du nombre de threads.

## <a name="inefficient-io"></a>E/S inefficace

![E&#47;O inefficace](../profiling/media/inefficient_io.png "Inefficient_IO")

L’utilisation abusive ou la mauvaise utilisation des E/S est une cause fréquente de l’inefficacité des applications. Regardez l’illustration précédente. Le profil de la chronologie visible montre que 44 % du temps de thread visible sont consommés par les E/S. La chronologie montre de grandes quantités d’E/S, ce qui indique que l’application profilée est fréquemment bloquée par les E/S. Pour obtenir des informations détaillées sur les types d’E/S dont il s’agit et sur l’endroit où votre programme se bloque, zoomez sur les zones problématiques, examinez le profil de chronologie visible, puis cliquez sur un bloc d’E/S spécifique pour afficher les piles d’appels en cours.

## <a name="lock-convoys"></a>Convois de verrouillage

![Convois de verrous](../profiling/media/lock_convoys.png "Lock_Convoys")

Les convois de verrouillage se produisent lorsque l’application acquiert des verrous dans un ordre de premier arrivé, premier servi, alors que le taux d’arrivée au verrou est supérieur au taux d’acquisition. La combinaison de ces deux conditions provoque l’envoi de demandes de sauvegarde au verrou. Une des méthodes possibles pour résoudre ce problème consiste à utiliser des verrous inéquitables, qui permettent au premier thread qui les trouve à l’état déverrouillé de les acquérir. L’illustration précédente montre ce comportement de convoi. Pour résoudre ce problème, essayez de réduire le nombre de conflits au niveau des objets de synchronisation et d’utiliser des verrous inéquitables.

## <a name="see-also"></a>Voir aussi

[vue Threads](../profiling/threads-view-parallel-performance.md)