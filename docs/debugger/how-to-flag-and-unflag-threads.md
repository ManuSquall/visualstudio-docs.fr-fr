---
title: Comment-baliser et supprimer l’indicateur de threads | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- treads, switching [debugging]
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7480f953e2fca57c296d6d1641059993bfa582c
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85349625"
---
# <a name="how-to-flag-and-unflag-threads-c-visual-basic-c"></a>Guide pratique pour baliser et supprimer l’indicateur de threads (C#, Visual Basic, C++)

Vous pouvez marquer un thread auquel vous souhaitez accorder une attention particulière en le marquant avec une icône dans les fenêtres **Threads**, **Piles parallèles** (vue thread), **Espion parallèle**et **Threads GPU** . Cette icône vous aide, ainsi que d'autres, à distinguer les threads avec indicateur des autres threads.

Les threads avec indicateur reçoivent également un traitement spécial dans la liste des **Threads** de la barre d’outils **emplacement de débogage** et dans les autres fenêtres de débogage multithread. Vous pouvez afficher tous les threads ou uniquement les threads avec indicateur dans la liste des **Threads** ou dans les autres fenêtres.

### <a name="to-flag-or-unflag-a-thread"></a>Pour marquer ou supprimer l'indicateur d'un thread

- Dans la fenêtre **Threads** ou **Espion parallèle** , recherchez le thread qui vous intéresse, puis cliquez sur l’icône d’indicateur pour activer ou désactiver l’indicateur.
- Dans la fenêtre **Piles parallèles** , cliquez avec le bouton droit sur un thread ou un groupe de threads, puis sélectionnez ** \<thread> indicateur/** ou sans **indicateur/ \<thread> **.

### <a name="to-unflag-all-threads"></a>Pour supprimer tous les indicateurs de thread

- Dans la fenêtre **Threads**, cliquez avec le bouton droit sur un thread, puis cliquez sur **Tous les threads sans indicateur**.
- Dans la fenêtre **Espion parallèle** , sélectionnez tous les threads avec indicateur, puis cliquez avec le bouton droit et sélectionnez **Supprimer l’indicateur**.

### <a name="to-display-only-flagged-threads"></a>Pour afficher seulement les threads avec indicateur

- Choisissez le bouton **afficher les threads avec indicateur uniquement** dans l’une des fenêtres de débogage multithread.

### <a name="to-flag-just-my-code"></a>Pour signaler Uniquement mon code

1. Dans la barre d’outils en haut de la fenêtre **Threads**, cliquez sur l’icône d’indicateur.

2. Dans la liste déroulante, cliquez sur **Signaler uniquement mon code**.

### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>Pour signaler des threads associés aux modules sélectionnés

1. Dans la barre d’outils de la fenêtre **Threads**, cliquez sur l’icône d’indicateur.

2. Dans la liste déroulante, cliquez sur **Signaler la sélection de modules personnalisés**.

3. Dans la boîte de dialogue **Sélectionner les modules**, sélectionnez les modules souhaités.

4. (Facultatif) Dans la zone **Rechercher**, saisissez une chaîne pour rechercher des modules spécifiques.

5. Cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi
- [Déboguer les applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Bien démarrer avec le débogage d’applications multithreads](../debugger/get-started-debugging-multithreaded-apps.md)
- [Procédure pas à pas : déboguer des applications multithread à l’aide de la fenêtre threads](../debugger/how-to-use-the-threads-window.md)