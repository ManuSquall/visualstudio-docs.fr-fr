---
title: "Fonctionnement des valeurs de donn&#233;es de conflit de ressources dans les outils de profilage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "méthode de profilage d’accès concurrentiel"
  - "outils de profilage, méthode de concurrence"
ms.assetid: 071c0f0f-1eba-4dc8-ae87-0810e4086dd0
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Fonctionnement des valeurs de donn&#233;es de conflit de ressources dans les outils de profilage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le profilage de conflit de ressources collecte les informations de pile d'appels détaillées chaque fois que des threads concurrents dans une application sont convertis pour attendre l'accès à une ressource partagée.  
  
 **Conditions requises**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Les rapports de conflit de ressources affichent le nombre total de conflits et la durée totale d'attente pour une ressource pour les modules, fonctions, lignes de code source et instructions.  
  
-   Les valeurs inclusives affichent le nombre total de conflits \(par conflits de ressources\) qui ont forcé une fonction à attendre et la durée totale d'attente de la fonction.  Les conflits causés par des fonctions enfants appelées par la fonction ne sont pas inclus dans les valeurs inclusives.  
  
-   Les valeurs exclusives affichent uniquement le nombre de conflits qui ont forcé une fonction à attendre et qui ont été provoqués par le code dans le corps de la fonction.  Les conflits provoqués par les fonctions enfants ne sont pas inclus.  La durée exclusive pour la fonction inclut également uniquement les temps d'attente provoqués par les instructions dans le corps de la fonction.  
  
 Les vues de rapport de conflit de ressources incluent également des graphiques de chronologie qui affichent les événements de conflit individuels sur une période donnée et affichent les piles d'appels qui ont créé l'événement particulier.  Pour plus d'informations, consultez l'une des rubriques suivantes :  
  
-   [Détails relatifs au thread, vue](../profiling/thread-details-view-contention-data.md)  
  
-   [Vue Informations sur les ressources](../profiling/resource-details-view-contention-data.md)  
  
 Pour plus d'informations sur le deuxième mode de profilage d'accès concurrentiel, consultez [Visualiseur concurrence](../profiling/concurrency-visualizer.md).