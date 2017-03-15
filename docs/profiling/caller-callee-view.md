---
title: "Mode Appelant/Appel&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.callercallee"
helpviewer_keywords: 
  - "outils de profilage, rapports, mode Appelant/Appelé"
  - "outils de profilage, mode Appelant/Appelé"
  - "rapports de performances, mode Appelant/Appelé"
  - "Appelant/Appelé, mode"
ms.assetid: d3511bcf-cce0-4cbe-aecb-b94c7c80ad1b
caps.latest.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 32
---
# Mode Appelant/Appel&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le mode Appelant\/Appelé affiche les informations de profilage d'une fonction sélectionnée et ses fonctions parents et enfants.  Le mode Appelant\/Appelé contient trois grilles :  
  
 **Fonction actuelle** s'affiche dans la grille centrale et contient les informations de profilage de la fonction sélectionnée.  Les valeurs comprennent tous les appels à la fonction collectés dans l'exécution du profilage.  
  
 **Fonctions qui ont appelé la fonction active** est affiché dans la grille supérieure et indique le nombre de valeurs de la fonction sélectionnée \(actuelle\) générées par les appels de la fonction d'appelant \(parent\).  
  
 **Fonctions qui ont été appelées par la fonction active** s'affiche dans la grille inférieure et indique les informations de profilage des fonctions d'appelé \(enfant\) de la fonction sélectionnée lorsque la fonction enfant a été appelée par la fonction actuelle.  
  
 Les colonnes disponibles en mode Appelant\/Appelé dépendent de la méthode de profilage \(échantillonnage ou instrumentation\) utilisée pour collecter les données et de la collecte ou non des données de mémoire .NET dans l'exécution du profilage.  
  
 Vous pouvez sélectionner une fonction différente comme Fonction active dans la partie centrale de la fenêtre du mode Rapport en double\-cliquant sur l'une des fonctions répertoriées dans les deux autres parties de la fenêtre.  Le mode Rapport est mis à jour automatiquement pour refléter les modifications.  
  
 Vous pouvez trier les données en cliquant sur les noms de colonnes.  Des colonnes supplémentaires peuvent être ajoutées au mode Appelant\/Appelé.  Pour plus d’informations, consultez [Comment : personnaliser les colonnes de la vue de rapport](../profiling/how-to-customize-report-view-columns.md).  
  
## Voir aussi  
 [Mode Appelant\/Appelé](../profiling/caller-callee-view-sampling-data.md)   
 [Mode Appelant\/Appelé](../profiling/caller-callee-view-instrumentation-data.md)   
 [Mode Appelant\/Appelé \- instrumentation](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Mode Appelant\/Appelé \- échantillonnage](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Mode Appelant\/Appelé](../profiling/caller-callee-view-contention-data.md)