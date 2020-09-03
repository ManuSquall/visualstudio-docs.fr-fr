---
title: Affichage des threads GPU dans le débogueur | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cbbb49a1017fb0bc65300f3c16050db4954e1103
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85348715"
---
# <a name="how-to-use-the-gpu-threads-window-c"></a>Comment : utiliser la fenêtre threads GPU (C++)
Dans la fenêtre Threads GPU, vous pouvez visualiser et utiliser les threads qui s'exécutent sur le GPU dans l'application que vous déboguez. Pour plus d’informations sur les applications qui s’exécutent sur le GPU, consultez [C++ amp vue d’ensemble](/cpp/parallel/amp/cpp-amp-overview).

 La fenêtre Threads GPU contient une table dans laquelle chaque ligne représente un ensemble de threads GPU qui ont les mêmes valeurs dans toutes les colonnes. Vous pouvez trier, réorganiser, supprimer et regrouper les éléments qui figurent dans les colonnes. Vous pouvez marquer ou supprimer l'indicateur, figer et libérer (reprendre) les threads à partir de la fenêtre Threads GPU. Les colonnes suivantes sont affichées dans la fenêtre Threads GPU :

- La colonne d'indicateur, où vous pouvez marquer un thread auquel vous souhaitez apporter une attention spéciale.

- Colonne de thread actuelle, dans laquelle une flèche jaune indique le thread actuel.

- Colonne **Nombre de threads**, qui affiche le nombre de threads au même emplacement.

- Colonne **Ligne**, qui affiche la ligne de code où chaque groupe de threads est situé.

- Colonne **Adresse**, qui affiche l’adresse d’instruction où chaque groupe de threads est localisé. Par défaut, cette colonne est masquée.

- Colonne **Emplacement**, qui est l’emplacement dans le code source.

- Colonne **État**, qui indique si le thread est actif, bloqué, non démarré ou terminé.

- Colonne **Mosaïque**, qui indique l’index de mosaïque des threads dans la ligne.

  L'en-tête du tableau montre la mosaïque et le thread en cours d'affichage.

  [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-display-the-gpu-threads-window"></a>Pour afficher la fenêtre Threads GPU

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet, puis choisissez **Propriétés**.

2. Dans la fenêtre **Pages de propriétés** du projet, sous **Propriétés de configuration**, choisissez **Débogage**.

3. Dans la liste **Débogueur à lancer**, sélectionnez **Débogueur Windows local**. Dans la liste **Type de débogueur**, sélectionnez **GPU uniquement**. Vous devez choisir le débogueur pour désactiver des points d'arrêt dans le code qui s'exécute sur le GPU.

4. Choisissez le bouton **OK**.

5. Définissez un point d'arrêt dans le code GPU.

6. Dans la barre de menus, choisissez **Débogage**, puis **Démarrer le débogage**. Attendez que l'application atteigne le point d'arrêt.

7. Dans la barre de menus, choisissez **Déboguer**, **Fenêtres**, **Threads GPU**.

### <a name="to-switch-to-a-different-thread"></a>Pour basculer vers un autre thread

- Double-cliquez sur la colonne. (Raccourci : sélectionnez la ligne et choisissez Entrée.)

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
- [Déboguer les applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Comment : utiliser la fenêtre Espion parallèle](../debugger/how-to-use-the-parallel-watch-window.md)
- [Procédure pas à pas : débogage d’une application C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)