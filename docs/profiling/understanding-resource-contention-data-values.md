---
title: Présentation des valeurs des données de conflit de ressources | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3d62b21e83f057c2a1d2e4347b3d7bcf6dbc22ad
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53896626"
---
# <a name="understand-resource-contention-data-values"></a>Comprendre le fonctionnement des valeurs de données de contention de ressources

Le profilage de conflit de ressources collecte les informations détaillées de la pile des appels chaque fois que des threads en concurrence dans une application sont forcés d’attendre pour accéder à une ressource partagée.

Les rapports de conflit de ressources affichent le nombre total de conflits et le temps total passé en attente d’une ressource pour les modules, les fonctions, les lignes de code source et les instructions où l’attente s’est produite.

- Les valeurs inclusives affichent le nombre total de conflits qui ont forcé une fonction à attendre en raison des conflits de ressources et le temps d’attente total de la fonction.  Les conflits provoqués par des fonctions enfants qui ont été appelées par la fonction sont inclus dans les valeurs de temps inclusives.

- Les valeurs de temps exclusives montrent seulement le nombre de conflits qui ont forcé une fonction à attendre et qui ont été provoqués par le code du corps de la fonction. Les conflits provoqués par des fonctions enfants ne sont pas inclus. Le temps exclusif pour la fonction inclut seulement les temps d’attente qui ont été provoqués par des instructions du corps de la fonction.

Les vues du rapport de conflit de ressources incluent également des graphiques chronologiques qui montrent les événements de conflit individuels au fil du temps et affichent les piles d’appels qui ont créé l’événement particulier. Pour plus d'informations, consultez l'une des rubriques suivantes :

- [Informations relatives au thread, vue](../profiling/thread-details-view-contention-data.md)

- [Informations relatives à la ressource, vue](../profiling/resource-details-view-contention-data.md)

Pour plus d’informations sur le deuxième mode de profilage d’accès concurrentiel, consultez [Visualiseur concurrentiel](../profiling/concurrency-visualizer.md).