---
title: Affichage Threads GPU dans le débogueur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
- vs.debug.gputhreads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, GPU threads window
ms.assetid: c647c502-a9f0-48e0-a430-976744a5fa51
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c99e0e1bf64a6a88778d4bfcf27a796916a0f044
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-use-the-gpu-threads-window"></a>Comment : utiliser la fenêtre Threads GPU
Dans la fenêtre Threads GPU, vous pouvez visualiser et utiliser les threads qui s'exécutent sur le GPU dans l'application que vous déboguez. Pour plus d’informations sur les applications qui s’exécutent sur le GPU, consultez [présentation de C++ AMP](/cpp/parallel/amp/cpp-amp-overview).  
  
 La fenêtre Threads GPU contient une table dans laquelle chaque ligne représente un ensemble de threads GPU qui ont les mêmes valeurs dans toutes les colonnes. Vous pouvez trier, réorganiser, supprimer et regrouper les éléments qui figurent dans les colonnes. Vous pouvez marquer ou supprimer l'indicateur, figer et libérer (reprendre) les threads à partir de la fenêtre Threads GPU. Les colonnes suivantes sont affichées dans la fenêtre Threads GPU :  
  
-   La colonne d'indicateur, où vous pouvez marquer un thread auquel vous souhaitez apporter une attention spéciale.  
  
-   Colonne de thread active, dans laquelle une flèche jaune indique que le thread actuel.  
  
-   Le **le nombre de threads** colonne, qui affiche le nombre de threads au même emplacement.  
  
-   Le **ligne** colonne, qui affiche la ligne de code où se trouve chaque groupe de threads.  
  
-   Le **adresse** colonne qui affiche l’adresse d’instruction où chaque groupe de threads est localisé. Par défaut, cette colonne est masquée.  
  
-   Le **emplacement** colonne, qui est l’emplacement dans le code source.  
  
-   Le **état** colonne, ce qui indique si le thread est actif, bloqué, non démarré ou terminé.  
  
-   Le **vignette** colonne, ce qui indique l’index de mosaïque des threads dans la ligne.  
  
 L'en-tête du tableau montre la mosaïque et le thread en cours d'affichage.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-display-the-gpu-threads-window"></a>Pour afficher la fenêtre Threads GPU  
  
1.  Dans l' **Explorateur de solutions**, ouvrez le menu contextuel du projet et choisissez **Propriétés**.  
  
2.  Dans le **Pages de propriétés** fenêtre pour le projet, sous **propriétés de Configuration**, choisissez **débogage**.  
  
3.  Dans le **débogueur à lancer** liste, sélectionnez **débogueur Windows Local**. Dans le **Type de débogueur** liste, sélectionnez **GPU uniquement**. Vous devez choisir le débogueur pour désactiver des points d'arrêt dans le code qui s'exécute sur le GPU.  
  
4.  Sélectionnez le bouton **OK** .  
  
5.  Définissez un point d'arrêt dans le code GPU.  
  
6.  Dans la barre de menus, choisissez **Débogage**, puis **Démarrer le débogage**. Attendez que l'application atteigne le point d'arrêt.  
  
7.  Une barre de menus, choisissez **déboguer**, **Windows**, **Threads GPU**.  
  
### <a name="to-switch-to-a-different-thread"></a>Pour basculer vers un autre thread.  
  
-   Double-cliquez sur la colonne. (Raccourci : sélectionnez la ligne et choisissez Entrée.)  
  
### <a name="to-display-a-particular-tile-and-thread"></a>Pour afficher une mosaïque et un thread particuliers  
  
1.  Choisissez le **développer le sélecteur de Thread** dans la fenêtre Threads GPU.  
  
2.  Entrez les valeurs de mosaïque et de threads dans les zones de texte.  
  
3.  Cliquez sur le bouton qui dispose d'une flèche au-dessus de lui.  
  
### <a name="to-display-or-hide-a-column"></a>Pour afficher ou masquer une colonne  
  
-   Ouvrez le menu contextuel de la fenêtre Threads GPU, choisissez **colonnes**, puis choisissez la colonne que vous souhaitez afficher ou masquer.  
  
### <a name="to-sort-by-a-column"></a>Pour effectuer un tri en fonction d'une colonne  
  
-   Sélectionnez le titre de la colonne.  
  
### <a name="to-group-threads"></a>Pour regrouper des threads  
  
-   Ouvrez le menu contextuel de la fenêtre Threads GPU, choisissez **Group By**, puis choisissez un des noms de colonnes affichées. Choisissez **aucun** pour dissocier les threads.  
  
### <a name="to-freeze-or-thaw-a-row-of-threads"></a>Pour geler ou libérer une ligne de threads  
  
-   Ouvrez le menu contextuel pour la ligne et choisissez **Figer** ou **libérer**.  
  
### <a name="to-flag-or-unflag-a-row-of-threads"></a>Pour marquer une ligne de threads ou en supprimer l'indicateur  
  
-   Sélectionnez la colonne d’indicateur pour le thread, ou ouvrez le menu contextuel pour le thread et choisissez **indicateur** ou **supprimer l’indicateur**.  
  
### <a name="to-display-only-flagged-threads"></a>Pour afficher seulement les threads avec indicateur  
  
-   Cliquez sur le bouton indicateur dans la fenêtre Threads GPU.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage d’Applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Comment : utiliser la fenêtre Espion parallèle](../debugger/how-to-use-the-parallel-watch-window.md)   
 [Procédure pas-à-pas : débogage d’une application C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)