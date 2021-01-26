---
title: Choisir des événements d’échantillonnage | Microsoft Docs
description: Découvrez comment définir l’exemple d’événement pour répondre à vos besoins et définir le nombre de cycles entre les échantillons. Les événements disponibles incluent les cycles d’horloge et les défauts de page.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.sampling
helpviewer_keywords:
- clock cycles sample event
- sample events, choosing
- profiling tools, sample events
- page faults sample event
- system calls sample event
- performance counter sample event
- performance tools, sample events
ms.assetid: ce7cb734-80ac-4930-a4ef-e24395e1cc07
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ed97fd205ffc0c969d0cad39d962cd8cdeb4e2eb
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801573"
---
# <a name="how-to-choose-sampling-events"></a>Guide pratique pour choisir des événements d’échantillonnage
Par défaut, les outils de profilage de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] collectent les données de performances à un intervalle correspondant à un nombre de cycles processeur utilisés par le processus profilé. Le nombre de cycles par défaut dans un intervalle est de 10 000 000, ce qui correspond approximativement à 0,01 seconde sur un ordinateur 1 GHz. Vous pouvez modifier le nombre de cycles d’un intervalle, ainsi que l’événement d’échantillon. Les événements d’échantillons suivants sont disponibles :

- Cycles d’horloge - Pour les problèmes lié au processeur.

- Défauts de page - Pour les problèmes liés à la mémoire.

- Appels système - Pour les problèmes d’E/S.

- Compteurs de performances - Compteurs UC pour les problèmes de performances.

> [!IMPORTANT]
> Lorsque vous collectez des données de mémoire .NET (allocations, durées de vie d’objets, ou les deux) à l’aide de la méthode d’échantillonnage, tous les événements d’échantillonnage spécifiés par l’utilisateur sont ignorés, et les événements d’allocation de mémoire et de garbage collection appropriés sont utilisés pour collecter des données.

### <a name="to-select-a-sample-event"></a>Pour sélectionner un événement d’échantillon

1. Dans l’ **Explorateur de performances**, cliquez avec le bouton droit sur la session de performance, puis cliquez sur **Propriétés**.

2. Dans les **Pages de propriétés**, cliquez sur les propriétés **Échantillonnage**.

3. Dans la liste déroulante **Événement d’échantillon**, sélectionnez l’événement d’échantillon à utiliser pour profiler votre application.

    > [!NOTE]
    > Les **compteurs de performances disponibles** sont activés uniquement si vous sélectionnez **Compteur de performances** dans la liste déroulante **Événement d’échantillon**.

4. Si vous sélectionnez **Compteur de performances**, sélectionnez un compteur UC dans le contrôle arborescence **Compteurs de performance disponibles**.

    - Les compteurs situés sous le nœud **Événements portables** sont disponibles sur tous les types de processeurs.

    - Les compteurs situés sous le nœud **Événements de plateforme** sont spécifiques au processeur de l’ordinateur actuel et peuvent ne pas être disponibles sur d’autres types de processeurs.

5. Lorsque vous sélectionnez un événement d’échantillon, une valeur d’intervalle d’échantillonnage par défaut s’affiche dans la zone de texte **Intervalle d’échantillonnage**. Si nécessaire, vous pouvez entrer la valeur de votre choix dans la zone de texte.

## <a name="see-also"></a>Voir aussi
- [Configurer des sessions de performance](../profiling/configuring-performance-sessions.md)
- [Comment : choisir des méthodes de collection](../profiling/how-to-choose-collection-methods.md)
- [Compteurs UC et Windows](../profiling/cpu-and-windows-counters.md)
- [Comprendre le fonctionnement des valeurs de données d’échantillonnage](../profiling/understanding-sampling-data-values.md)
- [Profiler à partir de la ligne de commande](../profiling/using-the-profiling-tools-from-the-command-line.md)
