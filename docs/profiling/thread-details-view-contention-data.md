---
title: "Vue D&#233;tails relatifs au thread - donn&#233;es de conflit du profileur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.threaddetails"
helpviewer_keywords: 
  - "Détails relatifs au thread (vue)"
ms.assetid: 874c3b1c-88d8-479a-bb35-1291d9aa8e67
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Vue D&#233;tails relatifs au thread - donn&#233;es de conflit du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vue Détails relatifs au thread présente un graphique de chronologie des événements bloquants dans le thread sélectionné d'une exécution du profilage provoqués par des conflits sur des ressources.  Un événement bloquant se produit lorsque le thread est forcé d'interrompre l'exécution car un autre thread a verrouillé l'accès à une ressource.  
  
 Cette vue représente la chronologie d'exécution du thread sous la forme d'une barre horizontale et les événements bloquants sous la forme d'une barre verticale sur une chronologie horizontale pour le thread.  Lorsque cela est nécessaire, vous pouvez effectuer un zoom sur une section de la chronologie pour afficher les événements individuels.  Pour afficher le chemin d'exécution des fonctions qui ont provoqué l'événement, cliquez sur la barre d'événement.  Les fonctions s'affichent dans la fenêtre Pile des appels.  Lorsque le code source d'une fonction est disponible, cliquez sur le nom de la fonction pour modifier le fichier source dans l'interface de Visual Studio.  
  
## Navigation dans la chronologie  
  
#### Pour effectuer un zoom sur un segment de chronologie  
  
-   Cliquez et faites glisser le pointeur de la souris pour sélectionner une zone de la chronologie.  
  
     Lorsque vous relâchez la souris, la vue effectue un zoom sur le segment sélectionné.  Vous pouvez répéter ce processus pour zoomer encore davantage.  La case de défilement de la barre de défilement représente la taille relative du segment de temps affiché dans la vue.  
  
#### Pour effectuer un zoom arrière sur une chronologie  
  
-   Cliquez sur **Zoom arrière** pour revenir au niveau de zoom précédent.  
  
-   Cliquez sur **Réinitialisation du zoom** pour afficher l'intégralité de la chronologie dans la vue.  
  
#### Pour afficher la pile des appels d'un événement  
  
-   Dans le graphique de chronologie, cliquez sur la barre verticale qui représente l'événement.  
  
#### Pour afficher ou modifier le code source d'une fonction dans la pile des appels  
  
-   Dans la fenêtre Pile des appels, cliquez sur le nom de la fonction.  
  
 Le code source de la fonction doit faire partie du projet actuel.  
  
#### Pour afficher les événements de conflit d'une ressource dans tous les threads dans l'exécution du profilage  
  
-   Dans le graphique de chronologie, cliquez sur le nom ou d'ID de la ressource.  
  
     La [Vue Informations sur les ressources](../profiling/resource-details-view-contention-data.md) s'ouvre pour la ressource sélectionnée.  
  
#### Pour consulter les données de conflit du thread dans la fenêtre Processus  
  
-   Dans le graphique de chronologie, cliquez sur **Total**.  
  
     La [Mode Processus](../profiling/process-view-contention-data.md) s'ouvre avec le thread sélectionné.