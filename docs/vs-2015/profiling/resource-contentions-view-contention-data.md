---
title: Mode Conflits de ressources - Données de conflit | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.view.resourcecontention
helpviewer_keywords:
- Resource Contentions view
ms.assetid: 14a7f774-211f-4ef8-af05-94d1c8f65d2f
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c6db867b582c4d1f5b0722d085e8a2eac48d182f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49253017"
---
# <a name="resource-contentions-view---contention-data"></a>Mode Conflits de ressources - Données de conflit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le mode Conflits de ressources répertorie des données de conflit pour les ressources qui étaient la source d’événements de conflit. Un événement de conflit se produit quand une fonction dans un thread est forcée à attendre l’accès à la ressource parce qu’une fonction dans un autre thread a acquis l’accès exclusif à la ressource. Chaque ressource est le nœud racine d’une arborescence des appels qui affiche les chemins d’exécution de fonctions qui ont entraîné les événements de conflit.  
  
## <a name="data-values"></a>Valeurs de données  
  
### <a name="resource-values"></a>Valeurs de ressources  
 Les données dans une ligne de ressource affichent la durée totale pendant laquelle l’accès à la ressource a été bloqué dans les données de profilage et le nombre total d’événements de conflit qui se sont produits à cause du conflit d’accès à cette ressource. Les valeurs inclusives et exclusives pour une ressource sont toujours les mêmes.  
  
### <a name="function-values"></a>Valeurs de fonction  
 Les valeurs de fonction sont basées sur les instances de la fonction qui se sont produites dans le chemin d’exécution représenté dans l’arborescence des appels.  
  
-   Les valeurs exclusives sont basées sur les événements qui se sont produits quand la fonction exécutait des instructions dans son corps de fonction. Les événements qui se sont produits dans les fonctions appelées par la fonction ne sont pas inclus dans les valeurs exclusives.  
  
-   Les valeurs inclusives sont basées sur les événements qui se sont produits quand la fonction ou une fonction appelée par la fonction s’exécutait.  
  
### <a name="percentage-values"></a>Valeurs de pourcentage  
 Les valeurs de pourcentage sont basées sur la durée totale ou les événements de conflit dans les données de profilage. Si le rapport ou la vue de l’exécution du profilage est filtré, seuls le temps bloqué et les conflits dans les données filtrées sont utilisés comme valeur totale.  
  
## <a name="navigating-the-resource-allocation-view"></a>Navigation dans l’affichage Répartition des ressources  
  
|Colonne|Description|  
|------------|-----------------|  
|**Name**|Nom de la ressource ou de la fonction.|  
|**Temps bloqué exclusif**|-   Pour une ressource, durée totale pendant laquelle l’accès à la ressource a été bloqué et a provoqué l’attente d’un thread.<br />-   Pour une fonction, durée pendant laquelle ces instances de la fonction n’ont pas pu accéder à la ressource parente quand la fonction exécutait le code dans le corps de la fonction. Le temps bloqué dans les fonctions qui ont été appelées par la fonction n’est pas inclus.|  
|**% de temps bloqué exclusif**|-   Pour une ressource, pourcentage de tout le temps bloqué dans les données de profilage qui était du temps bloqué de cette ressource.<br />-   Pour une fonction, pourcentage de tout le temps bloqué dans les données de profilage qui était du temps bloqué exclusif de ces instances de fonction.|  
|**Conflits exclusifs**|-   Pour une ressource, nombre total de fois où l’accès à la ressource a été bloqué et a provoqué l’attente d’un thread.<br />-   Pour une fonction, nombre de fois où ces instances de la fonction n’ont pas pu accéder à la ressource parente quand la fonction exécutait le code dans le corps de la fonction. Les événements bloquants dans les fonctions qui ont été appelées par la fonction ne sont pas inclus.|  
|**% de conflits exclusifs**|-   Pour une ressource, pourcentage de tous les événements de conflit dans les données de profilage qui étaient des événements de conflit pour l’accès à cette ressource.<br />-   Pour une fonction, pourcentage de tous les événements de conflit dans les données de profilage qui étaient des événements de conflit exclusifs de ces instances de fonction pour la ressource parente.|  
|**Temps bloqué inclusif**|-   Pour une ressource, durée totale pendant laquelle l’accès à la ressource a été bloqué et a provoqué l’attente d’un thread.<br />-   Pour une fonction, durée pendant laquelle ces instances de la fonction ou de toute fonction appelée par les instances n’ont pas pu accéder à la ressource parente quand la fonction exécutait le code dans le corps de la fonction.|  
|**% de temps bloqué inclusif**|-   Pour une ressource, pourcentage de tout le temps bloqué dans les données de profilage qui était du temps bloqué de cette ressource.<br />-   Pour une fonction, pourcentage de tout le temps bloqué au cours de l’exécution de profilage qui était du temps bloqué inclusif de ces instances de fonction.|  
|**Conflits inclusifs**|-   Pour une ressource, nombre total de fois où l’accès à la ressource a été bloqué et a provoqué l’attente d’un thread.<br />-   Pour une fonction, pourcentage de tous les événements de conflit au cours de l’exécution de profilage qui étaient des événements de conflit inclusifs de ces instances de fonction pour la ressource parente.|  
|**% de conflits inclusifs**|-   Pour une ressource, pourcentage de tous les événements de conflit au cours de l’exécution de profilage qui étaient des événements de conflit pour l’accès à cette ressource.<br />-   Pour une fonction, nombre de fois où ces instances de la fonction n’ont pas pu accéder à la ressource parente quand la fonction exécutait le code dans le corps de la fonction. Les événements bloquants dans les fonctions qui ont été appelées par la fonction ne sont pas inclus.|  
|**Niveau**|Niveau d’imbrication de cette fonction dans l’arborescence des appels. Uniquement dans les rapports en ligne de commande [VSPerfReport](../profiling/vsperfreport.md).|  
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|  
|**Nom de module**|Nom du module qui contient la fonction.|  
|**Chemin de module**|Chemin d’accès du module qui contient la fonction.|  
|**ID de processus**|ID du processus (PID) dans lequel la fonction s’exécutait.|  
|**Nom du processus**|Nom du processus.|  
|**Fichier source**|Fichier source contenant la définition pour cette fonction.|



