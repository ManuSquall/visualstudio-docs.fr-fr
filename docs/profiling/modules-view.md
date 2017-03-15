---
title: "Modules, vue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.modules"
helpviewer_keywords: 
  - "Modules (vue)"
  - "rapports d'outils de profilage, Modules (vue)"
  - "outils de profilage, Modules (vue)"
ms.assetid: 4314a404-2120-425b-be42-180cd4bac840
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Modules, vue
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vue Modules répertorie les modules des données de profilage.  Chaque module correspond au nœud racine d'une arborescence hiérarchique.  Les fonctions profilées du module sont répertoriées sous le nœud de module.  Si les données de profilage ont été collectées à l'aide de la méthode d'échantillonnage, les informations de ligne figurent sous le nœud de fonction, tandis que les données de pointeur d'instruction figurent sous le nœud de ligne.  
  
 Développez ou réduisez le nom du module pour afficher ou fermer la vue des données de performances du module.  
  
 Pour ajouter ou supprimer des colonnes, cliquez avec le bouton droit dans la fenêtre de rapport, puis sélectionnez **Ajouter\/Supprimer des colonnes**.  Vous pouvez trier les données en cliquant sur un nom de colonne.  Pour plus d’informations, consultez [Comment : personnaliser les colonnes de la vue de rapport](../profiling/how-to-customize-report-view-columns.md).  
  
 Les colonnes disponibles en mode Modules dépendent de la méthode de profilage \(échantillonnage ou instrumentation\) utilisée pour collecter les données et de la collecte ou non des données de mémoire .NET dans l'exécution du profilage.  
  
## Voir aussi  
 [Modules, mode](../profiling/modules-view-sampling-data.md)   
 [Modules, vue](../profiling/modules-view-instrumentation-data.md)   
 [Vue Modules \- instrumentation](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Vue Modules \- échantillonnage](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Modules, vue](../profiling/modules-view-contention-data.md)