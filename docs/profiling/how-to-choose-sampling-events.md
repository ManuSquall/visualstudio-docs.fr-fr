---
title: "Guide pratique pour choisir des événements d’échantillonnage | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.property.sampling
helpviewer_keywords:
- clock cycles sample event
- sample events, choosing
- profiling tools, sample events
- page faults sample event
- system calls sample event
- performance counter sample event
- performance tools, sample events
ms.assetid: ce7cb734-80ac-4930-a4ef-e24395e1cc07
caps.latest.revision: "23"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8475544d6ecb822a25a423b73543d7364d79da10
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-choose-sampling-events"></a>Comment : choisir des événements d’échantillonnage
Par défaut, les outils de profilage de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] collectent les données de performances à un intervalle correspondant à un nombre de cycles processeur utilisés par le processus profilé. Le nombre de cycles par défaut dans un intervalle est de 10 000 000, ce qui correspond approximativement à 0,01 seconde sur un ordinateur 1 GHz. Vous pouvez modifier le nombre de cycles d’un intervalle, ainsi que l’événement d’échantillon. Les événements d’échantillons suivants sont disponibles :  
  
-   Cycles d’horloge - Pour les problèmes lié au processeur.  
  
-   Défauts de page - Pour les problèmes liés à la mémoire.  
  
-   Appels système - Pour les problèmes d’E/S.  
  
-   Compteurs de performances - Compteurs UC pour les problèmes de performances.  
  
> [!IMPORTANT]
>  Lorsque vous collectez des données de mémoire .NET (allocations, durées de vie d’objets, ou les deux) à l’aide de la méthode d’échantillonnage, tous les événements d’échantillonnage spécifiés par l’utilisateur sont ignorés, et les événements d’allocation de mémoire et de garbage collection appropriés sont utilisés pour collecter des données.  
  
### <a name="to-select-a-sample-event"></a>Pour sélectionner un événement d’échantillon  
  
1.  Dans l’ **Explorateur de performances**, cliquez avec le bouton droit sur la session de performance, puis cliquez sur **Propriétés**.  
  
2.  Dans les **Pages de propriétés**, cliquez sur les propriétés **Échantillonnage**.  
  
3.  Dans la liste déroulante **Événement d’échantillon**, sélectionnez l’événement d’échantillon à utiliser pour profiler votre application.  
  
    > [!NOTE]
    >  Les **compteurs de performances disponibles** sont activés uniquement si vous sélectionnez **Compteur de performances** dans la liste déroulante **Événement d’échantillon**.  
  
4.  Si vous sélectionnez **Compteur de performances**, sélectionnez un compteur UC dans le contrôle arborescence **Compteurs de performance disponibles**.  
  
    -   Les compteurs situés sous le nœud **Événements portables** sont disponibles sur tous les types de processeurs.  
  
    -   Les compteurs situés sous le nœud **Événements de plateforme** sont spécifiques au processeur de l’ordinateur actuel et peuvent ne pas être disponibles sur d’autres types de processeurs.  
  
5.  Lorsque vous sélectionnez un événement d’échantillon, une valeur d’intervalle d’échantillonnage par défaut s’affiche dans la zone de texte **Intervalle d’échantillonnage**. Si nécessaire, vous pouvez entrer la valeur de votre choix dans la zone de texte.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de sessions de performance](../profiling/configuring-performance-sessions.md)   
 [Guide pratique pour choisir une méthode de collecte](../profiling/how-to-choose-collection-methods.md)   
 [Compteurs UC et Windows](../profiling/cpu-and-windows-counters.md)   
 [Fonctionnement des valeurs de données d’échantillonnage](../profiling/understanding-sampling-data-values.md)   
 [Profilage à partir de la ligne de commande](../profiling/using-the-profiling-tools-from-the-command-line.md)