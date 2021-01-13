---
title: Définir un espion sur les variables dans les threads parallèles | Microsoft Docs
description: Définissez un espion sur les variables dans les threads parallèles dans Visual Studio. Affichez simultanément les valeurs qu’une expression contient sur plusieurs threads.
ms.custom: SEO-VS-2020
ms.date: 04/25/2017
ms.topic: how-to
f1_keywords:
- vs.debug.parallelwatch
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel watch window
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 28aeffb629a44c296fb9a349e165c7ce88f70b0c
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150572"
---
# <a name="set-a-watch-on-variables-in-parallel-threads-in-visual-studio-c-visual-basic-c"></a>Définir un espion sur les variables dans les threads parallèles dans Visual Studio (C#, Visual Basic, C++)
Dans la fenêtre Espion parallèle, vous pouvez simultanément afficher les valeurs qu'une expression contient sur plusieurs threads. Chaque ligne représente un thread s'exécutant dans une application, mais un thread peut être représenté dans plusieurs lignes. Plus spécifiquement, chaque ligne représente un appel de fonction dont la signature de la fonction correspond à la fonctionnalité sur le frame de pile actuel. Vous pouvez trier, réorganiser, supprimer et regrouper les éléments qui figurent dans les colonnes. Vous pouvez marquer ou supprimer l'indicateur, figer et libérer (reprendre) les threads. Les colonnes suivantes sont affichées dans la fenêtre **Espion parallèle** :

- La colonne d'indicateur, où vous pouvez marquer un thread auquel vous souhaitez apporter une attention spéciale.

- Colonne de thread actuelle, dans laquelle une flèche jaune indique le thread actuel (une flèche verte avec un point d’ancrage indique qu’un thread non actuel a le contexte de débogueur actuel).

- Une colonne configurable qui peut afficher l’ordinateur, le processus, la mosaïque, la tâche et le thread.

  > [!TIP]
  > Pour afficher les informations de tâche dans la fenêtre **Espion parallèle** , vous devez d’abord ouvrir la fenêtre de **tâche** .

- Les colonnes *Ajouter un espion* vides, dans lesquelles vous pouvez entrer des expressions à surveiller.

  [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-display-the-parallel-watch-window"></a>Pour afficher la fenêtre Espion parallèle

1. Définissez un point d'arrêt dans le code.

2. Dans la barre de menus, choisissez **Débogage**, puis **Démarrer le débogage**. Attendez que l'application atteigne le point d'arrêt.

3. Dans la barre de menus, sélectionnez **Déboguer**, **Fenêtres**, **Espion parallèle**, puis sélectionnez une fenêtre Espion. Vous pouvez ouvrir quatre fenêtres maximum.

### <a name="to-add-a-watch-expression"></a>Pour ajouter une expression espionne

- Sélectionnez l’une des colonnes *Ajouter un espion* vide, puis entrez une expression espionne.

### <a name="to-flag-or-unflag-a-thread"></a>Pour marquer ou supprimer l'indicateur d'un thread

- Sélectionnez la colonne d’indicateur pour la ligne (première colonne), ou ouvrez le menu contextuel du thread et choisissez **marquer ou supprimer** l' **indicateur**.

### <a name="to-display-only-flagged-threads"></a>Pour afficher seulement les threads avec indicateur

- Choisissez le bouton **afficher uniquement les indicateurs** dans l’angle supérieur gauche de la fenêtre **Espion parallèle** .

### <a name="to-switch-to-another-thread"></a>Pour basculer vers un autre thread

- Double-cliquez sur la colonne thread en cours (deuxième colonne). (Raccourci : sélectionnez la ligne et appuyez sur Entrée.)

### <a name="to-sort-a-column"></a>Pour trier une colonne

- Sélectionnez le titre de la colonne.

### <a name="to-group-threads"></a>Pour regrouper des threads

- Ouvrez le menu contextuel de la fenêtre Espion parallèle, choisissez **Grouper par**, puis l’élément de sous-menu approprié.

### <a name="to-freeze-or-thaw-threads"></a>Pour figer ou libérer les threads

- Ouvrez le menu contextuel de la ligne par défaut et choisissez **Figer** ou **Libérer**.

### <a name="to-export-the-data-in-the-parallel-watch-window"></a>Pour exporter les données dans la fenêtre Espion parallèle

- Cliquez sur le bouton **Ouvrir dans Excel**, puis sélectionnez **Ouvrir dans Excel** ou **Exporter au format CSV**.

### <a name="to-filter-by-a-boolean-expression"></a>Pour filtrer en fonction d'une expression booléenne

- Entrez une expression booléenne dans la zone **Filtrer par expression booléenne**. Le débogueur évalue l'expression de chaque contexte de thread. Seules les lignes avec la valeur `true` sont affichées.

## <a name="see-also"></a>Voir aussi
- [Déboguer des applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Comment : utiliser la fenêtre threads GPU](../debugger/how-to-use-the-gpu-threads-window.md)
- [Procédure pas à pas : débogage d’une application C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)