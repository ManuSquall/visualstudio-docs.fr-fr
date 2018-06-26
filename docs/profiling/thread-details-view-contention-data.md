---
title: Informations relatives au thread, vue - Données de conflit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.threaddetails
helpviewer_keywords:
- Thread Details view
ms.assetid: 874c3b1c-88d8-479a-bb35-1291d9aa8e67
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 712fcfa369c4a324554bda38df671dab1a95a1f5
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34477351"
---
# <a name="thread-details-view---contention-data"></a>Informations relatives au thread, vue - Données de conflit
La vue Détails du Thread présente un graphique chronologique des événements bloquants dans le thread sélectionné d’une exécution du profilage, qui ont été provoqués par des conflits sur les ressources. Un événement de blocage se produit quand le thread est forcé d’interrompre l’exécution, car un autre thread a verrouillé l’accès à une ressource.  
  
 Cette vue représente la chronologie de l’exécution du thread sous la forme d’une barre horizontale et les événements de blocage sous la forme de barres verticales sur une chronologie horizontale pour le thread. Quand c’est nécessaire, vous pouvez effectuer un zoom avant sur une section de la chronologie pour voir les événements individuels. Pour afficher le chemin d’exécution des fonctions qui ont provoqué l’événement, cliquez sur la barre de l’événement. Les fonctions apparaissent dans la fenêtre **Pile des appels**. Quand le code source d’une fonction est disponible, vous pouvez cliquer sur le nom de la fonction pour modifier le fichier source dans l’IDE Visual Studio.  
  
## <a name="navigate-the-timeline"></a>Naviguer dans la chronologie  
  
#### <a name="to-zoom-in-on-a-timeline-segment"></a>Pour faire un zoom sur un segment de la chronologie  
  
-   Cliquez et faites glisser le pointeur de la souris pour sélectionner une zone de la chronologie.  
  
     Quand vous relâchez la souris, la vue effectue un zoom avant sur le segment de temps sélectionné. Vous pouvez répéter le processus pour obtenir plus détails. La case de défilement sur la barre de défilement chronologique représente la taille relative de l’intervalle de temps qui est affiché dans la vue.  
  
#### <a name="to-zoom-out-on-a-timeline"></a>Pour appliquer un zoom arrière sur une chronologie  
  
-   Cliquez sur **Zoom arrière** pour revenir au niveau de zoom précédent.  
  
-   Cliquez sur **Réinitialisation du zoom** pour afficher l’intégralité de la chronologie de la vue.  
  
#### <a name="to-view-the-call-stack-of-an-event"></a>Pour afficher la pile des appels d’un événement  
  
-   Dans le graphe de chronologie, cliquez sur la barre verticale qui représente l’événement.  
  
#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>Pour afficher ou modifier le code source d’une fonction dans la pile des appels  
  
-   Dans la fenêtre **Pile des appels**, cliquez sur le nom de la fonction.  
  
 Le code source de la fonction doit faire partie du projet actif.  
  
#### <a name="to-view-the-contention-events-of-a-resource-in-all-threads-in-the-profiling-run"></a>Pour voir les événements de conflit d’une ressource dans tous les threads de l’exécution du profilage  
  
-   Dans le graphe de chronologie, cliquez sur le nom ou l’ID de la ressource.  
  
     La [vue Informations sur les ressources](../profiling/resource-details-view-contention-data.md) apparaît pour la ressource sélectionnée.  
  
#### <a name="to-view-the-thread-contention-data-in-the-processes-window"></a>Pour voir les données de conflit du thread dans la fenêtre Processus  
  
-   Dans le graphique chronologique, cliquez sur **Total**.  
  
     La [vue Processus](../profiling/process-view-contention-data.md) apparaît affiche avec le thread sélectionné.