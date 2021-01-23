---
title: Gérer des canaux | Documents Microsoft
description: Découvrez comment vous pouvez organiser les canaux pour votre processus afin de pouvoir examiner des modèles particuliers dans la vue threads du visualiseur concurrentiel.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.tools.managechannels
helpviewer_keywords:
- Concurrency Visualizer, Manage Channels
ms.assetid: 507b06e9-bb56-4a72-8fd5-f91f958da6fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b0dd8643f63a7a3e67400f09f00b999fff33f09e
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721266"
---
# <a name="manage-channels"></a>Gérer les canaux
Dans la **vue Threads** du visualiseur concurrentiel, vous pouvez organiser les canaux pour votre processus afin de pouvoir examiner des modèles particuliers. Vous pouvez trier les canaux, les déplacer vers le haut et vers le bas, ainsi que les masquer ou les afficher.

## <a name="sort-by"></a>Trier par
 Vous pouvez utiliser le contrôle Trier par pour trier les threads selon différents critères, en fonction du niveau de zoom actuel. Cette fonction est particulièrement utile quand vous recherchez un modèle particulier. Vous pouvez effectuer le tri selon les critères suivants :

|Critères|Définition|
|--------------|----------------|
|Heure de Début|Trie les threads sur leur heure de début. Il s’agit de l’ordre de tri par défaut.|
|Heure de fin|Trie les threads sur leur heure de fin.|
|Exécution|Trie les threads sur le pourcentage de temps consacré à l’exécution.|
|Synchronization|Trie les threads sur le pourcentage de temps consacré à la synchronisation.|
|E/S|Trie les threads sur le pourcentage de temps consacré aux E/S (lecture et écriture de données).|
|Veille|Trie les threads sur le pourcentage de temps passé en veille.|
|Pagination|Trie les threads sur le pourcentage de temps consacré à la pagination.|
|Anticipation|Trie les threads sur le pourcentage de temps consacré à l’anticipation.|
|Traitement de l'interface utilisateur|Trie les threads sur le pourcentage de temps consacré au traitement de l’interface utilisateur.|

## <a name="move-selected-channel-up-or-down"></a>Déplacer le canal sélectionné vers le haut ou vers le bas
 Vous pouvez utiliser ces contrôles pour déplacer un canal vers le haut ou vers le bas dans la liste. Par exemple, vous pourrez placer les canaux associés côte à côte pour faciliter l’examen d’un modèle particulier ou d’une relation inter-threads.

## <a name="move-selected-channel-to-top-or-bottom"></a>Déplacer le canal sélectionné en haut ou en bas
 Vous pouvez déplacer des canaux sélectionnés en haut ou en bas de la liste pour pouvoir examiner un modèle particulier, ou faire disparaître certains canaux quand vous en examinez d’autres.

## <a name="hide-selected-channels"></a>Masquer les canaux sélectionnés
 Choisissez ce contrôle pour masquer des canaux. Par exemple, si un thread est à 100 % de synchronisation pendant toute la durée de votre processus managé, vous pouvez le masquer pendant que vous analysez d’autres threads.

> [!NOTE]
> Masquer un thread le supprime également du temps de calcul, qui est affiché dans la légende active et dans les rapports de profils.

## <a name="show-all-channels"></a>Afficher tous les canaux
 Ce contrôle est actif quand un ou plusieurs canaux sont masqués. Si vous cliquez dessus, tous les éléments masqués sont affichés et réintégrés dans les calculs de temps.

## <a name="move-markers-to-top"></a>Déplacer les marqueurs en haut
 Si une trace contient des événements de marqueur, vous pouvez utiliser cette commande pour déplacer les canaux de marqueurs en haut de la chronologie. Leur ordre relatif est conservé.

## <a name="group-markers-by-thread"></a>Regrouper les marqueurs par thread
 Si une trace contient des événements de marqueur, vous pouvez utiliser cette commande pour regrouper des canaux de marqueurs sous le thread qui a généré les événements de marqueur.  Les canaux de disques sont déplacés en haut de la liste de canaux, et les canaux GPU sont déplacés en bas.

## <a name="see-also"></a>Voir aussi
- [Contrôle zoom (vue threads)](../profiling/zoom-control-threads-view.md)
- [Mode mesure activé/désactivé](../profiling/measure-mode-on-off.md)
- [vue Threads](../profiling/threads-view-parallel-performance.md)