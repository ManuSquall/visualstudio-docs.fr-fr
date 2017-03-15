---
title: "DA0017&#160;: taux &#233;lev&#233;s de pagination de la m&#233;moire active sur le disque | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.17"
  - "vs.performance.rules.DA0017"
  - "vs.performance.DA0017"
ms.assetid: 01011eec-5930-43b3-980d-2cb01e2ca7f6
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# DA0017&#160;: taux &#233;lev&#233;s de pagination de la m&#233;moire active sur le disque
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID de la règle|DA0017|  
|Catégorie|Mémoire et pagination|  
|Méthode de profilage|Tous|  
|Message|Taux élevé de pagination de la mémoire active sur le disque.  Votre application peut être liée à la mémoire.|  
|Type de règle|Information|  
  
 Lorsque vous profilez en utilisant les méthodes d'échantillonnage, de mémoire. NET ou de conflits de ressources, vous devez collecter au moins 10 échantillons pour déclencher cette règle.  
  
## Cause  
 Les données des performances système collectées dans l'exécution du profilage indiquent qu'un taux élevé de mémoire active de pagination vers le disque et à partir du disque a été relevé dans toute l'exécution du profilage.  Les taux de pagination à ce niveau auront normalement un impact sur les performances et la réactivité de l'application.  Envisagez de réduire les allocations de mémoire en modifiant les algorithmes.  Il vous faudra peut\-être également prendre en compte les besoins en mémoire de votre application.  
  
## Description de la règle  
  
> [!NOTE]
>  Cette règle d'information se déclenche lorsque les niveaux de pagination de la mémoire active atteignent un niveau significatif.  En cas de niveau très élevé de pagination, c'est la règle d'avertissement [DA0014 : Taux élevés de pagination de la mémoire active sur le disque](../Topic/DA0014:%20Extremely%20high%20rates%20of%20paging%20active%20memory%20to%20disk.md) qui se déclenche à la place.  
  
 Une pagination excessive sur le disque peut être provoquée par une mémoire physique insuffisante.  Si les opérations de pagination dominent l'utilisation du disque physique sur lequel le fichier d'échange réside, elles peuvent ralentir les autres opérations de disque orientées application sur le même disque.  
  
 Les pages sont souvent lues à partir du disque ou écrites sur le disque dans le cadre d'opérations de pagination en bloc.  Le nombre de pages sorties par seconde est souvent beaucoup plus important que le nombre de pages écrites par seconde, par exemple.  Cela est dû au fait que le nombre de pages sorties par seconde inclut également les pages de données modifiées provenant du cache de fichier système.  Toutefois, ce n'est pas toujours facile de déterminer quel processus est directement responsable de la pagination ou pourquoi.  
  
## Comment corriger les violations  
 Double\-cliquez sur le message dans la fenêtre Liste d'erreurs pour naviguer jusqu'à l'affichage [Marques](../profiling/marks-view.md).  Recherchez la colonne **Mémoire\\Pages\/s**.  Déterminez s'il existe des phases spécifiques d'exécution du programme pendant lesquelles l'activité d'E\/S de pagination est plus importante que d'autres.  
  
 Si vous rassemblez les données de profil pour une application ASP.NET dans un scénario de test de charge, essayez d'exécuter à nouveau le test de charge sur un ordinateur configuré avec une mémoire physique \(ou RAM\) supplémentaire.  
  
 Envisagez de réduire les allocations de mémoire en modifiant les algorithmes et en évitant les API consommant beaucoup de mémoire telles que String.Concat et String.Substring.