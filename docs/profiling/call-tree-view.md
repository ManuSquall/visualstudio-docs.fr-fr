---
title: "Mode Arborescence des appels | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.calltree"
helpviewer_keywords: 
  - "mode Arborescence des appels"
  - "rapports de performances, mode Arborescence des appels"
  - "rapports d'outils de profilage, mode Arborescence des appels"
  - "outils de profilage, mode Arborescence des appels"
ms.assetid: b2dbc033-bf95-4d10-8e51-f9462979133e
caps.latest.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 34
---
# Mode Arborescence des appels
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vue Arborescence des appels affiche les chemins d'accès d'exécution des fonctions parcourus dans l'application profilée.  La racine de l'arborescence correspond au point d'entrée de l'application ou du composant.  Chaque nœud de fonction répertorie toutes les fonctions appelées et les données de performance liées à ces appels de fonction.  
  
 La vue Arborescence des appels peut également être développée pour mettre en surbrillance le chemin d'exécution d'une fonction qui a exigé le plus de temps ou qui a été échantillonnée le plus souvent.  Pour afficher le chemin le plus performant, cliquez avec le bouton droit sur la fonction, puis cliquez sur **Développer le chemin réactif**.  
  
 Chaque processus de l'exécution du profilage s'affiche sous la forme d'un nœud racine.  Vous pouvez définir le nœud initial du mode Arborescence des appels en cliquant avec le bouton droit sur le nœud que vous souhaitez définir comme nœud initial, puis en sélectionnant **Définir la racine**.  
  
 En définissant le nœud racine, vous supprimez toutes les autres entrées de l'affichage, à l'exception de la sous\-arborescence du nœud sélectionné.  Vous pouvez réinitialiser le nœud racine sur le nœud que vous affichiez.  Dans la fenêtre Mode Arborescence des appels, cliquez avec le bouton droit, puis sélectionnez **Réinitialiser la racine**.  
  
 La vue Arborescence des appels peut être personnalisée pour l'ajout ou la suppression de colonnes.  Cliquez avec le bouton droit sur la **barre de titre Nom de la colonne**, puis sélectionnez **Ajouter\/Supprimer des colonnes**.  
  
 La vue Arborescence des appels peut être configurée pour l'atténuation du bruit en limitant la quantité de données présentées.  L'utilisation de la fonction de réduction du bruit permet de rendre les problèmes de performances plus visibles.  Lorsque les problèmes de performances sont faciles à distinguer, l'analyse en est facilitée.  Pour plus d’informations, consultez [Comment : configurer la réduction du bruit dans les vues des rapports](../profiling/how-to-configure-noise-reduction-in-report-views.md).  
  
> [!NOTE]
>  Si l'atténuation du bruit est configurée pour afficher un avertissement lorsqu'elle est activée, une barre d'information s'affiche dans le rapport.  
  
 Pour plus d'informations sur les définitions des colonnes dans la vue Arborescence des appels, consultez les références suivantes :  
  
 [Mode Arborescence des appels](../profiling/call-tree-view-sampling-data.md)  
  
 [Mode Arborescence des appels](../profiling/call-tree-view-instrumentation-data.md)  
  
 [Mode Arborescence des appels \- échantillonnage](../profiling/call-tree-view-dotnet-memory-sampling-data.md)  
  
 [Mode Arborescence des appels](../profiling/call-tree-view-contention-data.md)  
  
## Voir aussi  
 [Vues des rapports d’outils de profilage](../profiling/performance-report-views.md)   
 [Fonctionnement des valeurs de données d’instrumentation](../profiling/understanding-instrumentation-data-values.md)   
 [Fonctionnement des valeurs de données d’échantillonnage](../profiling/understanding-sampling-data-values.md)