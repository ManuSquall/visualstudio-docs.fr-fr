---
title: "Vue Informations sur les ressources - donn&#233;es de conflit du profileur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.resourcedetails"
helpviewer_keywords: 
  - "Informations sur les ressources (vue)"
ms.assetid: a4ecfe1c-abbc-4fb3-9ab2-34de50486901
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Vue Informations sur les ressources - donn&#233;es de conflit du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vue Informations sur les ressources présente un graphique de chronologie des événements bloquants provoqués par les conflits sur une ressource sélectionnée.  Un événement bloquant se produit lorsqu'un thread est forcé d'interrompre son exécution parce qu'un autre thread a verrouillé l'accès à la ressource.  
  
 Cette vue représente la chronologie d'exécution de chaque thread sous la forme d'une barre horizontale et chaque événement bloquant sous la forme d'une barre verticale sur la chronologie du thread.  Si nécessaire, vous pouvez agrandir un segment de la chronologie pour consulter des événements individuels.  Pour afficher le chemin d'exécution \(pile des appels\) des fonctions qui ont provoqué l'événement, cliquez sur la barre d'événement.  Les fonctions s'affichent dans la fenêtre **Pile des appels**.  Lorsque le code source d'une fonction est disponible, vous pouvez cliquer sur le nom de la fonction pour modifier le fichier source dans l'interface de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Procédures  
  
#### Pour agrandir un segment de chronologie  
  
-   Faites glisser le pointeur de la souris sur une zone de la chronologie.  
  
     Lorsque vous relâchez le bouton de la souris, la vue effectue un zoom sur le segment sélectionné.  Vous pouvez répéter le processus pour accentuer le zoom sur le segment.  La case de défilement de la barre de défilement représente la taille relative du segment chronologique affiché dans la vue.  
  
#### Pour effectuer un zoom arrière sur une chronologie  
  
-   Effectuez l'une des étapes suivantes :  
  
    -   Cliquez sur **Zoom arrière** pour revenir au niveau de zoom précédent.  
  
    -   Cliquez sur **Réinitialisation du zoom** pour afficher l'intégralité de la chronologie dans la vue.  
  
#### Pour afficher la pile des appels d'un événement  
  
-   Dans le graphique de chronologie, cliquez sur la barre d'événement.  
  
#### Pour afficher ou modifier le code source d'une fonction dans la pile des appels  
  
-   Dans la fenêtre **Pile des appels**, cliquez sur le nom de la fonction.  
  
 Le code source de la fonction doit faire partie du projet actuel.  
  
#### Pour consulter l'arborescence des appels des événements de conflit pour la ressource  
  
-   Dans le graphique de chronologie, cliquez sur **Total**.  
  
     La vue Conflits s'affiche pour la ressource.  Pour plus d'informations, consultez [Mode Conflits de ressources](../profiling/resource-contentions-view-contention-data.md).  
  
#### Pour afficher tous les événements de conflit d'un thread  
  
-   Dans le graphique de chronologie, cliquez sur le nom ou l'ID du thread.  
  
     La vue Détails relatifs au thread apparaît pour le thread sélectionné.  Pour plus d’informations, consultez [Détails relatifs au thread, vue](../profiling/thread-details-view-contention-data.md).