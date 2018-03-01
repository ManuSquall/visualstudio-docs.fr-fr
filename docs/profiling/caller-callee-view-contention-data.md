---
title: "Vue Appelant/Appelé - Données de conflit | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Caller/Callee view
ms.assetid: a18a1b1b-9b39-43c7-b1f3-708fd20376f6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 47e4f57ffac71d6fb4f1c3e8cd8176c80d9f002a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="caller--callee-view----contention-data"></a>Vue Appelant/Appelé - Données de conflit
La vue Appelant/Appelé affiche des données de conflit pour la fonction sélectionnée, ainsi que pour ses fonctions parentes et enfants. La vue Appelant/Appelé comprend trois grilles.  
  
 La grille centrale intitulée **Fonction active** contient les informations de conflit associées à la fonction sélectionnée. Les valeurs incluent tous les conflits bloquants pour la fonction.  
  
 La grille supérieure intitulée **Fonctions qui ont appelé la fonction active** contient les contributions de chaque fonction appelante (parent) aux valeurs de la fonction sélectionnée (active).  
  
 La grille inférieure intitulée **Fonctions qui ont été appelées par la fonction active** contient des informations de conflit pour les fonctions appelées (enfants) de la fonction sélectionnée quand la fonction enfant a été appelée par la fonction active.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Type**|Contexte de la fonction :<br /><br /> -   **0** : fonction active<br />-   **1** : fonction qui appelle la fonction active<br />-   **2** : fonction qui est appelée par la fonction active<br /><br /> Uniquement dans les rapports en ligne de commande [VSPerfReport](../profiling/vsperfreport.md).|  
|**Temps bloqué exclusif**|-   Pour la fonction active, durée pendant laquelle cette fonction n’a pas pu exécuter de code dans le corps de la fonction. Le temps bloqué dans les fonctions appelées par la fonction n’est pas inclus.<br />-   Pour une fonction appelante, partie du temps bloqué exclusif de la fonction active qui s’est produit quand cette fonction a appelé la fonction active.<br />-   Pour une fonction appelée, durée pendant laquelle cette fonction n’a pas pu exécuter son propre code quand cette fonction a été appelée par la fonction active. Le temps bloqué dans les fonctions enfants appelées par la fonction appelée n’est pas inclus.|  
|**% de temps bloqué exclusif**|Pourcentage de tout le temps bloqué au cours de l’exécution de profilage qui était du temps bloqué exclusif pour cette fonction dans ce contexte.|  
|**Conflits exclusifs**|-   Pour la fonction active, nombre de fois où cette fonction n’a pas pu exécuter de code dans le corps de la fonction. Les conflits qui se sont produits dans les fonctions appelées par la fonction ne sont pas inclus.<br />-   Pour une fonction appelante, nombre de conflits exclusifs de la fonction active qui se sont produits quand cette fonction a appelé la fonction active.<br />-   Pour une fonction appelée, nombre de fois où cette fonction n’a pas pu exécuter de code dans le corps de la fonction quand cette fonction a été appelée par la fonction active. Les conflits qui se sont produits dans les fonctions appelées par la fonction appelante ne sont pas inclus.|  
|**% de conflits exclusifs**|Pourcentage de tous les conflits au cours de l’exécution de profilage qui étaient des conflits exclusifs pour cette fonction dans ce contexte.|  
|**Adresse de la fonction**|Adresse de la fonction ou jeton.|  
|**Nom de la fonction**|Nom complet de la fonction.|  
|**Temps bloqué inclusif**|-   Pour la fonction active, durée pendant laquelle cette fonction ou l’une des fonctions appelées par cette fonction n’a pas pu s’exécuter. Le temps bloqué dans les fonctions qui ont été appelées par la fonction active est inclus.<br />-   Pour une fonction appelante, partie du temps bloqué inclusif de la fonction active qui s’est produit quand cette fonction a appelé la fonction active.<br />-   Pour une fonction appelée, durée pendant laquelle cette fonction ou l’une des fonctions appelées par la fonction n’a pas pu s’exécuter quand cette fonction a été appelée par la fonction active. Le temps bloqué dans les fonctions qui ont été appelées par la fonction appelée est inclus.|  
|**% de temps bloqué inclusif**|Pourcentage de tout le temps bloqué au cours de l’exécution de profilage qui était du temps bloqué inclusif pour cette fonction dans ce contexte.|  
|**Conflits inclusifs**|-   Pour la fonction active, nombre de fois où cette fonction ou l’une des fonctions appelées par la fonction n’a pas pu s’exécuter. Les conflits qui se sont produits dans les fonctions appelées par la fonction sont inclus.<br />-   Pour une fonction appelante, nombre de conflits inclusifs de la fonction active qui se sont produits quand cette fonction a appelé la fonction active.<br />-   Pour une fonction appelée, nombre de fois où cette fonction ou l’une des fonctions appelées par la fonction n’a pas pu s’exécuter quand cette fonction a été appelée par la fonction active. Les conflits qui se sont produits dans les fonctions appelées par la fonction appelante sont inclus.|  
|**% de conflits inclusifs**|Pourcentage de tous les conflits au cours de l’exécution de profilage qui étaient des conflits exclusifs pour cette fonction dans ce contexte.|  
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|  
|**Nom de module**|Nom du module qui contient la fonction.|  
|**Chemin de module**|Chemin d’accès du module qui contient la fonction.|  
|**ID du processus**|ID du processus (PID) dans lequel les conflits se sont produits.|  
|**Nom du processus**|Nom du processus.|  
|**Nom de fonction racine**|Nom de la fonction active. Uniquement dans les rapports en ligne de commande [VSPerfReport](../profiling/vsperfreport.md).|  
|**Fichier source**|Fichier source contenant la définition pour cette fonction.|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour personnaliser les colonnes de la vue Rapport](../profiling/how-to-customize-report-view-columns.md)   
 [Vue Appelant/Appelé](../profiling/caller-callee-view.md)   
 [Vue Appelant/Appelé - Données d’échantillonnage](../profiling/caller-callee-view-sampling-data.md)   
 [Vue Appelant/Appelé - Données d’instrumentation de la mémoire .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Vue Appelant/Appelé - Données d’échantillonnage de mémoire .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Vue Appelant/appelé - Données d’instrumentation](../profiling/caller-callee-view-instrumentation-data.md)