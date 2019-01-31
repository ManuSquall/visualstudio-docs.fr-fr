---
title: 'Procédure : Collecter les données des compteurs UC | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.cpucounters
helpviewer_keywords:
- profiling tools, using portable CPU counters
- performance tools, portable CPU counters
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae991730caf5e83e9632d7b9a871a62778463098
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54928566"
---
# <a name="how-to-collect-cpu-counter-data"></a>Procédure : Collecter les données des compteurs UC

Un compteur d’événements UC sert à collecter des données de performances matérielles. Cet article vous montre comment collecter des données de compteur d’événements quand vous utilisez la méthode de profilage par instrumentation.

Il existe deux types d’événements de compteur UC :

- Événements portables : événements UC pouvant être collectés, quel que soit le processeur.

- Événements de plateforme : événements UC associés à un processeur particulier.

  Les événements portables sont des événements généraux, tels que des instructions retirées, des cycles hors interruption, des événements de mémoire tampon UC, des événements de branche et des événements du cache L2. Les compteurs d’événements de plateforme disponibles dépendent du fabricant du processeur.

  Les catégories d’événements peuvent être partagées entre les compteurs d’événements portables et de plateforme. Par exemple, les catégories de données suivantes sont souvent communes aux deux types :

- Événements mémoire

- Événements frontaux

- Événements de branche

  Vous pouvez collecter les données de compteur de performances de deux manières dans le profileur :

- Collecter des données à partir d’un ou plusieurs compteurs lors d’un profilage par instrumentation

- Spécifier un événement de compteur comme intervalle d’échantillonnage lors d’un profilage par échantillonnage Pour plus d'informations, voir [Procédure : Choisir des événements d’échantillonnage](../profiling/how-to-choose-sampling-events.md).

## <a name="to-collect-cpu-performance-counter-data-when-you-profile-by-instrumentation"></a>Pour collecter des données de compteur de performances UC lors d’un profilage par instrumentation

1. Dans les **pages de propriétés** de la session de performance, cliquez sur **Compteurs UC**.

2. Cochez la case **Collecter les compteurs UC**.

3. Développez l’arborescence **Compteurs de performance disponibles** jusqu’à ce que vous trouviez les événements d’échantillons que vous voulez collecter.

4. Pour chaque événement à collecter, sélectionnez l’événement, puis cliquez sur la flèche droite pour l’ajouter à la liste **Compteurs sélectionnés**.

    > [!NOTE]
    > L’option **Compteurs de performance disponibles** n’est activée que si vous cochez la case **Collecter les compteurs UC**.

## <a name="see-also"></a>Voir aussi

[Configurer des sessions de performances](../profiling/configuring-performance-sessions.md)  
[Propriétés d’une session de performance](../profiling/performance-session-properties.md)  
[Compteurs UC et Windows](../profiling/cpu-and-windows-counters.md)  
[Guide pratique pour choisir des événements d’échantillonnage](../profiling/how-to-choose-sampling-events.md)