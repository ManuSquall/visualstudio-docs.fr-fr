---
title: 'Comment : utiliser la fenêtre Threads GPU | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.gputthreads
- vs.debug.gputhreads
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, GPU threads window
ms.assetid: c647c502-a9f0-48e0-a430-976744a5fa51
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a747ec02e8b47649e42ec8fcb600de97f549c105
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47507275"
---
# <a name="how-to-use-the-gpu-threads-window"></a>Comment : utiliser la fenêtre Threads GPU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [affichage des Threads GPU dans le débogueur](https://docs.microsoft.com/visualstudio/debugger/how-to-use-the-gpu-threads-window).  
  
Dans la fenêtre Threads GPU, vous pouvez visualiser et utiliser les threads qui s'exécutent sur le GPU dans l'application que vous déboguez. Pour plus d’informations sur les applications qui s’exécutent sur le GPU, consultez [présentation de C++ AMP](http://msdn.microsoft.com/library/9e593b06-6e3c-43e9-8bae-6d89efdd39fc).  
  
 La fenêtre Threads GPU contient une table dans laquelle chaque ligne représente un ensemble de threads GPU qui ont les mêmes valeurs dans toutes les colonnes. Vous pouvez trier, réorganiser, supprimer et regrouper les éléments qui figurent dans les colonnes. Vous pouvez marquer ou supprimer l'indicateur, figer et libérer (reprendre) les threads à partir de la fenêtre Threads GPU. Les colonnes suivantes sont affichées dans la fenêtre Threads GPU :  
  
-   La colonne d'indicateur, où vous pouvez marquer un thread auquel vous souhaitez apporter une attention spéciale.  
  
-   Colonne de thread active, où une flèche jaune indique un thread actif. Flèche désignant un thread sur lequel l'exécution s'est arrêtée dans le débogueur.  
  
-   Le **le nombre de threads** colonne qui affiche le nombre de threads au même emplacement.  
  
-   Le **ligne** colonne qui affiche la ligne de code où se trouve chaque groupe de threads.  
  
-   Le **adresse** colonne qui affiche l’adresse d’instruction où se trouve chaque groupe de threads. Par défaut, cette colonne est masquée.  
  
-   Le **emplacement** colonne, qui est l’emplacement dans le code source.  
  
-   Le **état** colonne, ce qui indique si le thread est actif, bloqué, non démarré ou complète.  
  
-   Le **vignette** colonne, ce qui indique l’index de la mosaïque pour les threads dans la ligne.  
  
 L'en-tête du tableau montre la mosaïque et le thread en cours d'affichage.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-display-the-gpu-threads-window"></a>Pour afficher la fenêtre Threads GPU  
  
1.  Dans l' **Explorateur de solutions**, ouvrez le menu contextuel du projet et choisissez **Propriétés**.  
  
2.  Dans le **Pages de propriétés** fenêtre pour le projet, sous **propriétés de Configuration**, choisissez **débogage**.  
  
3.  Dans le **débogueur à lancer** liste, sélectionnez **débogueur Windows Local**. Dans le **Type de débogueur** liste, sélectionnez **GPU uniquement**. Vous devez choisir le débogueur pour désactiver des points d'arrêt dans le code qui s'exécute sur le GPU.  
  
4.  Sélectionnez le bouton **OK** .  
  
5.  Définissez un point d'arrêt dans le code GPU.  
  
6.  Dans la barre de menus, choisissez **Débogage**, puis **Démarrer le débogage**. Attendez que l'application atteigne le point d'arrêt.  
  
7.  Une barre de menus, choisissez **déboguer**, **Windows**, **Threads GPU**.  
  
### <a name="to-change-to-a-different-active-thread"></a>Pour passer à un autre thread actif  
  
-   Double-cliquez sur la colonne. (Raccourci : sélectionnez la ligne et choisissez Entrée.)  
  
### <a name="to-display-a-particular-tile-and-thread"></a>Pour afficher une mosaïque et un thread particuliers  
  
1.  Choisissez le **développer le sélecteur de Thread** bouton dans la fenêtre Threads GPU.  
  
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
 [Déboguer les Applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Comment : utiliser la fenêtre Espion parallèle](../debugger/how-to-use-the-parallel-watch-window.md)   
 [Procédure pas-à-pas : débogage d’une application C++ AMP](http://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)



