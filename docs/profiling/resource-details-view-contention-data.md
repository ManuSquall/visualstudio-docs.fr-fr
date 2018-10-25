---
title: Vue Informations sur les ressources - Données de conflit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.resourcedetails
helpviewer_keywords:
- Resource Details view
ms.assetid: a4ecfe1c-abbc-4fb3-9ab2-34de50486901
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 024241870bb4a0a2ef696130cbe5ddc94319493a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49837202"
---
# <a name="resource-details-view---contention-data"></a>Vue Informations sur les ressources - Données de conflit
La vue Informations sur les ressources présente un graphique chronologique des événements bloquants provoqués par des conflits sur une ressource sélectionnée. Un événement bloquant se produit quand un thread est forcé d’interrompre l’exécution, car un autre thread a verrouillé l’accès à une ressource.  
  
 Cette vue représente la chronologie d’exécution de chaque thread sous la forme d’une barre horizontale et chaque événement bloquant sous la forme d’une barre verticale sur la chronologie du thread. Si nécessaire, vous pouvez effectuer un zoom sur une section de la chronologie pour afficher les événements individuels. Pour afficher le chemin d’exécution (la pile des appels) des fonctions qui ont provoqué l’événement, cliquez sur la barre de l’événement. Les fonctions apparaissent dans la fenêtre **Pile des appels**. Quand le code source d’une fonction est disponible, vous pouvez cliquer sur le nom de la fonction pour modifier le fichier source dans l’interface de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-magnify-a-timeline-segment"></a>Pour effectuer un zoom sur un segment de chronologie  
  
-   Faites glisser le pointeur de la souris sur une zone de la chronologie.  
  
     Quand vous relâchez le bouton de la souris, la vue effectue un zoom avant sur l’intervalle de temps sélectionné. Vous pouvez répéter ce processus pour zoomer encore davantage. La case de défilement sur la barre de défilement chronologique représente la taille relative de l’intervalle de temps qui est affiché dans la vue.  
  
#### <a name="to-zoom-out-on-a-timeline"></a>Pour appliquer un zoom arrière sur une chronologie  
  
-   Effectuez l’une des opérations suivantes :  
  
    -   Cliquez sur **Zoom arrière** pour revenir au niveau de zoom précédent.  
  
    -   Cliquez sur **Réinitialisation du zoom** pour afficher l’intégralité de la chronologie dans la vue.  
  
#### <a name="to-view-the-call-stack-of-an-event"></a>Pour afficher la pile des appels d’un événement  
  
-   Dans le graphique chronologique, cliquez sur la barre de l’événement.  
  
#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>Pour afficher ou modifier le code source d’une fonction dans la pile des appels  
  
- Dans la fenêtre **Pile des appels**, cliquez sur le nom de la fonction.  
  
  Le code source de la fonction doit faire partie du projet actif.  
  
#### <a name="to-view-the-call-tree-of-contention-events-for-the-resource"></a>Pour afficher l’arborescence des appels des événements de conflit pour la ressource  
  
-   Dans le graphique chronologique, cliquez sur **Total**.  
  
     Le mode Conflits s’affiche pour la ressource. Pour plus d’informations, consultez [Mode Conflits de ressources](../profiling/resource-contentions-view-contention-data.md)  
  
#### <a name="to-view-all-the-contention-events-of-a-thread"></a>Pour afficher tous les événements de conflit d’un thread  
  
-   Dans le graphique chronologique, cliquez sur le nom ou l’ID du thread.  
  
     La vue Détails relatifs au thread apparaît pour le thread sélectionné. Pour plus d’informations, consultez [Vue Détails relatifs au thread](../profiling/thread-details-view-contention-data.md).