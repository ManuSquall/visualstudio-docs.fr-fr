---
title: Présentation des valeurs des données de conflit de ressources | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
ms.assetid: 071c0f0f-1eba-4dc8-ae87-0810e4086dd0
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5983396924f38c31b6dafcd42b762042e1880e8d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54784114"
---
# <a name="understanding-resource-contention-data-values"></a>Fonctionnement des valeurs de données de conflit de ressources
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le profilage de conflit de ressources collecte les informations détaillées de la pile des appels chaque fois que des threads en concurrence dans une application sont forcés d’attendre pour accéder à une ressource partagée.  
  
 **Spécifications**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Les rapports de conflit de ressources affichent le nombre total de conflits et le temps total passé en attente d’une ressource pour les modules, les fonctions, les lignes de code source et les instructions où l’attente s’est produite.  
  
- Les valeurs inclusives affichent le nombre total de conflits qui ont forcé une fonction à attendre en raison des conflits de ressources et le temps d’attente total de la fonction.  Les conflits provoqués par des fonctions enfants qui ont été appelées par la fonction sont inclus dans les valeurs de temps inclusives.  
  
- Les valeurs de temps exclusives montrent seulement le nombre de conflits qui ont forcé une fonction à attendre et qui ont été provoqués par le code du corps de la fonction. Les conflits provoqués par des fonctions enfants ne sont pas inclus. Le temps exclusif pour la fonction inclut seulement les temps d’attente qui ont été provoqués par des instructions du corps de la fonction.  
  
  Les vues du rapport de conflit de ressources incluent également des graphiques chronologiques qui montrent les événements de conflit individuels au fil du temps et affichent les piles d’appels qui ont créé l’événement particulier. Pour plus d'informations, consultez l'une des rubriques suivantes :  
  
- [Détails relatifs au thread, vue](../profiling/thread-details-view-contention-data.md)  
  
- [Informations sur les ressources, vue](../profiling/resource-details-view-contention-data.md)  
  
  Pour plus d’informations sur le deuxième mode de profilage d’accès concurrentiel, consultez [Visualiseur concurrentiel](../profiling/concurrency-visualizer.md).
