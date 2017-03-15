---
title: "Profil de temps de blocage, rapport | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.report.blocking"
helpviewer_keywords: 
  - "Visualiseur concurrentiel, rapport de profil de temps de blocage"
ms.assetid: 3bc45af0-3ba6-4fa3-a336-be8e9ae95107
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Profil de temps de blocage, rapport
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les rapports de profils fournissent des données de temps de blocage agrégée pour les piles des appels spécifiques à chaque catégorie de blocage \(par exemple « E\/S » ou « Synchronisation »\).  Le rapport de préemption liste les processes qui ont préempté le processus actuel ensemble avec le nombre d'instances de préemption.  Pour générer le rapport de profil bloquant, l'outil collecte des appels d'API de blocage et les accumule dans une arborescence de piles des appels.  Les données présentées dans ces rapports varient selon la plage horaire actuelle, les threads masqués et les deux filtres suivants qui peuvent être appliqués :  
  
-   Si Uniquement mon code est sélectionné, seules les frames de pile avec du code utilisateur sont présentées, ainsi qu'un niveau en dessous du code utilisateur.  
  
-   Si la valeur de réduction du bruit est définie, les piles assemblées dont la valeur de fréquence est inférieure à celle spécifiée sont ignorées.  
  
 Développez toute entrée de l'arborescence des appels pour rechercher la ligne de code correspondant au temps de blocage passé.  Pour localiser la ligne source pour une entrée, dans son menu contextuel, choisissez **Afficher la source**.  Pour localiser la ligne de code qui a appelé celui\-ci, dans le menu contextuel, choisissez **Afficher les sites d'appel**.  Si un seul site d'appel existe, la commande se déplace jusqu'à la ligne de code mise en surbrillance pour le site d'appel.  Si plusieurs sites d'appel sont disponibles, la commande ouvre une boîte de dialogue dans laquelle vous pouvez sélectionner une entrée puis choisir le bouton **Atteindre la source** pour localiser le site d'appel mis en surbrillance.  Il s'avère souvent très utile d'afficher le code source du site d'appel comportant le plus d'instances et\/ou le plus de temps.  
  
## Colonnes des rapports de temps de blocage  
 Le tableau suivant présente les colonnes de chaque rapport de temps de blocage.  
  
|Nom de la colonne|Description|  
|-----------------------|-----------------|  
|Nom|Nom de la fonction pour chaque niveau de la pile des appels.|  
|Instances|Nombre d'instances de l'appel bloquant pendant la période visible.|  
|Temps inclusif de blocage|Temps total de blocage passé pour toutes les piles qui atteignent ce niveau de l'arborescence de la pile d'appels.  Le temps inclusif correspond à la somme du temps de blocage exclusif pour cette fonction et du temps de blocage exclusif pour l'ensemble de ses nœuds enfants.|  
|Temps de blocage exclusif|Temps total de blocage pendant lequel cette fonction est resté au niveau le plus bas de la pile des appels.  Une entrée de pile d'appels unique dont la valeur de temps de blocage exclusif est élevée peut être une fonction intéressante pour le rapport.|  
|API\/Catégorie d'attente|Indiqué uniquement pour les fonctions situées au niveau le plus bas de la pile des appels.  Lorsque la signature de l'appel bloquant est reconnue, le nom de l'API bloquante est fourni.  Si la signature n'est pas reconnue, les informations qui sont fournies sont celles indiquées par le noyau.|  
|Détails|Nom qualifié complet de la fonction.  Inclut le nombre de lignes si celui\-ci est disponible.|  
  
### Synchronisation  
 Le rapport Synchronisation affiche les appels responsables du blocage des segments lors de la synchronisation, ainsi que les temps de blocage d'agrégation de chaque pile des appels.  Pour plus d’informations, consultez [Durée de synchronisation](../profiling/synchronization-time.md)  
  
### Sleep  
 Le rapport Veille affiche les appels responsables de temps de blocage attribué au temps de veille, ainsi que les temps de blocage d'agrégation de chaque pile des appels.  Pour plus d'informations, consultez [Durée de veille](../profiling/sleep-time.md).  
  
### E\/S  
 Le rapport E\/S affiche les appels responsables du blocage des segments sur les E\/S, ainsi que les temps de blocage d'agrégation de chaque pile des appels.  Pour plus d'informations, consultez [Temps d'E\/S \(vue Threads\)](../profiling/i-o-time-threads-view.md).  
  
### Gestion de la mémoire  
 Le rapport Gestion de la mémoire affiche les appels responsables du blocage des segments sur les opérations de gestion de la mémoire, ainsi que les temps de blocage d'agrégation de chaque pile des appels.  Pour plus d'informations, consultez [Période de gestion de la mémoire](../profiling/memory-management-time.md).  
  
### Préemption  
 Le rapport de préemption liste les processes qui ont préempté le processus actuel ensemble avec le nombre d'instances.  Vous pouvez développer chaque processus pour afficher les threads spécifiques qui ont remplacé des threads dans le processus actuel et afficher une répartition des instances de préemption par thread.  Ce rapport de blocage est moins exploitable que les autres parce que la préemption est généralement imposée sur votre processus par le système d'exploitation, pas par un problème dans votre code.  Pour plus d'informations, consultez [Durée de préemption](../profiling/preemption-time.md).  
  
### Traitement IU  
 Le rapport Traitement IU affiche les appels responsables du blocage des segments sur les blocs de traitement IU, ainsi que les temps de blocage d'agrégation de chaque pile des appels.  Pour plus d'informations, consultez [Temps de traitement UI](../profiling/ui-processing-time.md).  
  
## Voir aussi  
 [vue Threads](../profiling/threads-view-parallel-performance.md)