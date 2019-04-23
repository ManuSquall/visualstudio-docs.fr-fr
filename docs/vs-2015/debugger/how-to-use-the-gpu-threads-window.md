---
title: 'Procédure : Utilisez la fenêtre Threads GPU | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dcb55ee2128d237c2be6f57da828ec3c5877cfdd
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60044516"
---
# <a name="how-to-use-the-gpu-threads-window"></a>Procédure : Utiliser la fenêtre Threads GPU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans la fenêtre Threads GPU, vous pouvez visualiser et utiliser les threads qui s'exécutent sur le GPU dans l'application que vous déboguez. Pour plus d’informations sur les applications qui s’exécutent sur le GPU, consultez [présentation de C++ AMP](http://msdn.microsoft.com/library/9e593b06-6e3c-43e9-8bae-6d89efdd39fc).  
  
 La fenêtre Threads GPU contient une table dans laquelle chaque ligne représente un ensemble de threads GPU qui ont les mêmes valeurs dans toutes les colonnes. Vous pouvez trier, réorganiser, supprimer et regrouper les éléments qui figurent dans les colonnes. Vous pouvez marquer ou supprimer l'indicateur, figer et libérer (reprendre) les threads à partir de la fenêtre Threads GPU. Les colonnes suivantes sont affichées dans la fenêtre Threads GPU :  
  
- La colonne d'indicateur, où vous pouvez marquer un thread auquel vous souhaitez apporter une attention spéciale.  
  
- Colonne de thread active, où une flèche jaune indique un thread actif. Flèche désignant un thread sur lequel l'exécution s'est arrêtée dans le débogueur.  
  
- Colonne **Nombre de threads**, qui affiche le nombre de threads au même emplacement.  
  
- Colonne **Ligne**, qui affiche la ligne de code où chaque groupe de threads est situé.  
  
- Colonne **Adresse**, qui affiche l’adresse d’instruction où chaque groupe de threads est localisé. Par défaut, cette colonne est masquée.  
  
- Colonne **Emplacement**, qui est l’emplacement dans le code source.  
  
- Colonne **État**, qui indique si le thread est actif, bloqué, non démarré ou terminé.  
  
- Colonne **Mosaïque**, qui indique l’index de mosaïque des threads dans la ligne.  
  
  L'en-tête du tableau montre la mosaïque et le thread en cours d'affichage.  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-display-the-gpu-threads-window"></a>Pour afficher la fenêtre Threads GPU  
  
1. Dans l' **Explorateur de solutions**, ouvrez le menu contextuel du projet et choisissez **Propriétés**.  
  
2. Dans la fenêtre **Pages de propriétés** du projet, sous **Propriétés de configuration**, choisissez **Débogage**.  
  
3. Dans la liste **Débogueur à lancer**, sélectionnez **Débogueur Windows local**. Dans la liste **Type de débogueur**, sélectionnez **GPU uniquement**. Vous devez choisir le débogueur pour désactiver des points d'arrêt dans le code qui s'exécute sur le GPU.  
  
4. Sélectionnez le bouton **OK** .  
  
5. Définissez un point d'arrêt dans le code GPU.  
  
6. Dans la barre de menus, choisissez **Débogage**, puis **Démarrer le débogage**. Attendez que l'application atteigne le point d'arrêt.  
  
7. Dans la barre de menus, choisissez **Déboguer**, **Fenêtres**, **Threads GPU**.  
  
### <a name="to-change-to-a-different-active-thread"></a>Pour passer à un autre thread actif  
  
- Double-cliquez sur la colonne. (Clavier : Sélectionnez la ligne et appuyez sur ENTRÉE.)  
  
### <a name="to-display-a-particular-tile-and-thread"></a>Pour afficher une mosaïque et un thread particuliers  
  
1. Cliquez sur le bouton **Développer le sélecteur de thread** dans la fenêtre Threads GPU.  
  
2. Entrez les valeurs de mosaïque et de threads dans les zones de texte.  
  
3. Cliquez sur le bouton qui dispose d'une flèche au-dessus de lui.  
  
### <a name="to-display-or-hide-a-column"></a>Pour afficher ou masquer une colonne  
  
- Ouvrez le menu contextuel de la fenêtre Threads GPU, choisissez **Colonnes**, puis sélectionnez la colonne que vous souhaitez afficher ou masquer.  
  
### <a name="to-sort-by-a-column"></a>Pour effectuer un tri en fonction d'une colonne  
  
- Sélectionnez le titre de la colonne.  
  
### <a name="to-group-threads"></a>Pour regrouper des threads  
  
- Ouvrez le menu contextuel de la fenêtre Threads GPU, choisissez **Grouper par**, puis choisissez un des noms de colonnes affichés. Choisissez **Aucun** pour dissocier les threads.  
  
### <a name="to-freeze-or-thaw-a-row-of-threads"></a>Pour geler ou libérer une ligne de threads  
  
- Ouvrez le menu contextuel de la ligne par défaut et choisissez **Figer** ou **Libérer**.  
  
### <a name="to-flag-or-unflag-a-row-of-threads"></a>Pour marquer une ligne de threads ou en supprimer l'indicateur  
  
- Sélectionnez la colonne d’indicateur du thread, ou ouvrez le menu contextuel du thread et choisissez **Marquer** ou **Supprimer l’indicateur**.  
  
### <a name="to-display-only-flagged-threads"></a>Pour afficher seulement les threads avec indicateur  
  
- Cliquez sur le bouton indicateur dans la fenêtre Threads GPU.  
  
## <a name="see-also"></a>Voir aussi  
 [Déboguer les applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Guide pratique pour utiliser la fenêtre Espion parallèle](../debugger/how-to-use-the-parallel-watch-window.md)   
 [Procédure pas à pas : Débogage d’une Application C++ AMP](http://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)
