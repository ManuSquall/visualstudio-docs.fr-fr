---
title: Déboguer une application multithread
description: Déboguer à l’aide de la fenêtre Threads et la barre d’outils emplacement de débogage dans Visual Studio
ms.date: 11/21/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3a87fd0480727a524b36ab209f5126b0f996c30
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58790795"
---
# <a name="walkthrough-debug-a-multithreaded-app-using-the-threads-window-c-visual-basic-c"></a>Procédure pas à pas : Déboguer une application multithread à l’aide de la fenêtre Threads (C#, Visual Basic, C++)

Plusieurs éléments d’interface utilisateur Visual Studio vous aider à déboguer des applications multithreads. Cet article présente les fonctionnalités de débogage multithreads dans la fenêtre d’éditeur de code, **emplacement de débogage** barre d’outils, et **Threads** fenêtre. Pour plus d’informations sur les autres outils pour déboguer les applications multithreads, consultez [commencer le débogage d’applications multithreads](../debugger/get-started-debugging-multithreaded-apps.md).

Ce didacticiel ne prend que quelques minutes et vous permet de vous familiariser avec ses fondamentaux du débogage d’applications multithreads.

## <a name="create-a-multithreaded-app-project"></a>Créer un projet d’application multithread

Créer le projet d’application multithread suivant à utiliser dans ce didacticiel :

1. Ouvrez Visual Studio et créez un projet.

    ::: moniker range=">=vs-2019"
    Appuyez sur **Échap** pour fermer la fenêtre de démarrage. Type **Ctrl + Q** pour ouvrir la zone de recherche, tapez **console** (ou **c ++**), choisissez **modèles**, puis :

    - Pour C#, choisissez **créer un nouveau projet application Console (.NET Framework)** pour C#. Dans la boîte de dialogue qui apparaît, choisissez **Créer**.
    - Pour C++, choisissez **créer un nouveau projet application Console**. Dans la boîte de dialogue qui apparaît, choisissez **Créer**.

    Ensuite, tapez un nom tel que **MyThreadWalkthroughApp** et cliquez sur **créer**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet**. Dans le volet gauche de la **nouveau projet** boîte de dialogue, sélectionnez les éléments suivants :
    - Pour un C# application, sous **Visual C#** , choisissez **Windows Desktop**, puis, dans le volet central, choisissez **application Console (.NET Framework)**.
    - Pour un C++ application, sous **Visual C++** , choisissez **Windows Desktop**,, puis **Application de Console Windows**.

    Ensuite, tapez un nom tel que **MyThreadWalkthroughApp** et cliquez sur **OK**.
    ::: moniker-end

    Si vous ne voyez pas le modèle de projet **Application console**, accédez à **Outils** > **Obtenir les outils et fonctionnalités...**, qui ouvre Visual Studio Installer. Choisissez la charge de travail **Développement .NET Desktop** ou **Développement Desktop avec C++**, puis choisissez **Modifier**.

    Le nouveau projet s’affiche dans **l’Explorateur de solutions**, et un fichier source appelé *Program.cs* ou *MyThreadWalkthroughApp.cpp* s’ouvre dans la fenêtre de code source.

1. Remplacez le code dans le fichier source avec le C# ou C++ exemple de code à partir de [commencer le débogage d’applications multithreads](../debugger/get-started-debugging-multithreaded-apps.md).

1. Sélectionnez **fichier** > **Enregistrer tout**.

## <a name="start-debugging"></a>Démarrer le débogage

1. Recherchez les lignes suivantes dans le code source :

   ```csharp
   Thread.Sleep(3000);
   Console.WriteLine();
   ```

   ```C++
   Thread::Sleep(3000);
   Console.WriteLine();
   ```

1. Définir un point d’arrêt sur la `Console.WriteLine();` ligne en cliquant dans la marge gauche, ou en sélectionnant la ligne en appuyant sur **F9**.

   Le point d’arrêt apparaît comme un cercle rouge dans la marge gauche en regard de la ligne de code.

1. Sélectionnez **déboguer** > **démarrer le débogage**, ou appuyez sur **F5**.

   L’application démarre en mode débogage et s’arrête au point d’arrêt.

1. En mode arrêt, ouvrez le **Threads** en sélectionnant **déboguer** > **Windows** > **Threads**. Vous devez être dans une session de débogage pour ouvrir ou consultez le **Threads** et les autres fenêtres de débogage.

## <a name="examine-thread-markers"></a>Examiner les marqueurs de thread

1. Dans le code source, localisez le `Console.WriteLine();` ligne.

   1. Avec le bouton droit dans le **Threads** , puis sélectionnez **afficher les Threads dans la Source** ![afficher les Threads dans la Source](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") à partir du menu.

   La marge en regard du code source ligne affiche désormais un *marqueur de thread* icône ![marqueur de Thread](../debugger/media/dbg-thread-marker.png "marqueur de Thread"). Le marqueur de thread indique qu'un thread est interrompu à cet emplacement. S’il existe plusieurs threads arrêté à l’emplacement, le ![plusieurs threads](../debugger/media/dbg-multithreaded-show-threads.png "plusieurs threads") icône s’affiche.

1. Placez le pointeur sur le marqueur de thread. Un DataTip apparaît, affichant le numéro d’ID de nom et de thread pour le thread interrompu ou les threads. Les noms de thread peuvent être `<No Name>`.

   >[!TIP]
   >Pour aider à identifier les threads sans nom, vous pouvez les renommer dans le **Threads** fenêtre. Cliquez sur le thread et sélectionnez **renommer**.

1. Cliquez sur le marqueur de thread dans le code source pour afficher les options disponibles dans le menu contextuel.

## <a name="flag-and-unflag-threads"></a>Ajouter et supprimer des threads

Vous pouvez signaler des threads pour effectuer le suivi des threads à que vous conseille de prêter une attention particulière.

Indicateur et supprimer des threads à partir de l’éditeur de code source ou de la **Threads** fenêtre. Choisissez s’il faut afficher uniquement avec indicateur de threads ou tous les threads, à partir de la **emplacement de débogage** ou **Threads** barres d’outils de la fenêtre. Les sélections effectuées à partir de n’importe quel emplacement affectent tous les emplacements.

### <a name="flag-and-unflag-threads-in-source-code"></a>Indicateur et supprimer des threads dans le code source

1. Ouvrez le **emplacement de débogage** la barre d’outils en sélectionnant **vue** > **barres d’outils** > **emplacement de débogage**. Vous pouvez également avec le bouton droit dans la zone de barre d’outils et sélectionnez **emplacement de débogage**.

1. Le **emplacement de débogage** barre d’outils a trois champs : **Processus**, **Thread**, et **Frame de pile**. Liste déroulante la **Thread** liste, puis notez le nombre de threads. Dans le **Thread** liste, le thread en cours d’exécution est marqué par un **>** symbole.

1. Dans la fenêtre de code source, placez le curseur sur une icône de marqueur de thread dans la marge et sélectionnez l’icône d’indicateur (ou une des icônes d’indicateur vide) dans le DataTip. L’icône d’indicateur devient rouge.

   Vous pouvez également cliquer sur une icône de marqueur de thread, pointez sur **indicateur**, puis sélectionnez un thread à l’indicateur dans le menu contextuel.

1. Sur le **emplacement de débogage** barre d’outils, sélectionnez le **afficher uniquement les Threads avec indicateur** icône ![afficher les Threads avec indicateur](../debugger/media/dbg-threads-show-flagged.png "afficher les Threads avec indicateur"), à la droit de la **Thread** champ. L’icône est grisée, sauf si un ou plusieurs threads sont signalés.

   Seul le thread avec indicateur apparaît désormais dans le **Thread** liste déroulante dans la barre d’outils. Pour afficher de nouveau tous les threads, sélectionnez le **afficher uniquement les Threads avec indicateur** icône Nouveau.

   >[!TIP]
   >Une fois que vous avez marqué des threads, vous pouvez placer votre curseur dans l’éditeur de code, avec le bouton droit, puis sélectionnez **exécuter les Threads avec indicateur au curseur**. Veillez à choisir le code que tous les threads avec indicateur atteindront. **Exécuter les Threads avec indicateur jusqu’au curseur** va suspendre des threads sur la ligne sélectionnée de code, ce qui facilite contrôler l’ordre d’exécution par [gel et libération des threads](#bkmk_freeze).

1. Pour basculer l’état avec indicateur ou sans indicateur du thread en cours d’exécution, sélectionnez l’indicateur unique **l’état bascule actuel Thread avec indicateur** bouton de barre d’outils, à gauche de la **afficher uniquement les Threads avec indicateur** bouton. Marquer le thread actuel est utile pour localiser le thread actuel lors de l’affichant des threads avec indicateur uniquement.

1. Pour supprimer l’indicateur d’un thread, pointez sur le marqueur de thread dans le code source, puis sélectionnez l’icône de drapeau rouge à effacer, ou cliquez sur le marqueur de thread et sélectionnez **supprimer l’indicateur**.

### <a name="flag-and-unflag-threads-in-the-threads-window"></a>Indicateur et supprimer des threads dans la fenêtre Threads

Dans le **Threads** , threads avec indicateur doivent red indicateur des icônes en regard de celles-ci, tout en les threads sans indicateur, si indiqué, ont des icônes vides.

![Threads, fenêtre](../debugger/media/dbg-threads-window.png "Threads, fenêtre")

Sélectionnez une icône d’indicateur pour modifier l’état de thread avec indicateur ou sans indicateur, en fonction de son état actuel.

Vous pouvez également cliquez sur une ligne et sélectionnez **indicateur**, **supprimer l’indicateur**, ou **supprimer l’indicateur de tous les Threads** dans le menu contextuel.

Le **Threads** barre d’outils de la fenêtre a également un **afficher les Threads avec indicateur uniquement** bouton qui est le droit d’une des icônes d’indicateur de deux. Il fonctionne comme le bouton sur le **emplacement de débogage** barre d’outils et l’un des boutons contrôle l’affichage dans les deux emplacements.

### <a name="other-threads-window-features"></a>Autres fonctionnalités de la fenêtre Threads

Dans le **Threads** fenêtre, sélectionnez l’en-tête de n’importe quelle colonne pour trier les threads selon cette colonne. Sélectionnez à nouveau pour inverser l’ordre de tri. Si tous les threads sont affichés, en sélectionnant la colonne d’indicateur icône trie les threads avec indicateur ou sans indicateur de statut.

La deuxième colonne de la **Threads** fenêtre (avec aucun en-tête) est la **Thread en** colonne. Dans cette colonne une flèche jaune marque le point d’exécution actuel.

Le **emplacement** colonne montre où chaque thread s’affiche dans le code source. Sélectionnez la flèche de développement à côté du **emplacement** entrée, ou placez le curseur sur l’entrée, pour afficher une pile des appels partielle pour ce thread.

>[!TIP]
>Pour obtenir une vue graphique des piles d’appels des threads, utilisez la [piles parallèles](../debugger/using-the-parallel-stacks-window.md) fenêtre. Pour ouvrir la fenêtre, pendant le débogage, sélectionnez **déboguer**> **Windows** > **piles parallèles**.

En plus de **indicateur**, **supprimer l’indicateur**, et **supprimer l’indicateur de tous les Threads**, le menu contextuel pour **Thread** a des éléments de la fenêtre :

- Le **afficher les Threads dans la Source** bouton.
- **Affichage hexadécimal**, quelles modifications le **ID de Thread**s dans le **Threads** fenêtre du format décimal au format hexadécimal.
- [Commutateur à Thread](#switch-to-another-thread), qui bascule immédiatement l’exécution de ce thread.
- **Renommer**, ce qui vous permet de modifier le nom de thread.
- [Figer et libérer](#bkmk_freeze) commandes.

## <a name="bkmk_freeze"></a> Figer et libérer de l’exécution du thread

Figer et libérer, ou suspendre et reprendre des threads pour contrôler l’ordre dans lequel les threads exécutent le travail. Gel et libération des threads peuvent vous aider à résoudre les problèmes d’accès concurrentiel, tels que les interblocages et conditions de concurrence critique.

> [!TIP]
> Pour suivre un seul thread sans bloquer les autres threads, qui est également un scénario de débogage courantes, consultez [commencer le débogage d’applications multithread](../debugger/get-started-debugging-multithreaded-apps.md#bkmk_follow_a_thread).

**Pour figer et libérer des threads :**

1. Dans le **Threads** fenêtre, avec le bouton droit n’importe quel thread, puis sélectionnez **Figer**. Un **Pause** icône dans le **Thread actuel** colonne indique que le thread est figé.

1. Sélectionnez **colonnes** dans le **Threads** barre d’outils de la fenêtre, puis sélectionnez **compteur suspendu** pour afficher le **compteur suspendu** colonne. La valeur de compteur suspendu pour le thread figé est **1**.

1. Cliquez sur le thread figé et sélectionnez **libérer**.

   Le **Pause** icône disparaît et la **compteur suspendu** valeur change à **0**.

## <a name="switch-to-another-thread"></a>Basculer vers un autre thread

Vous pouvez voir un **l’application est en mode arrêt** fenêtre lorsque vous essayez de basculer vers un autre thread. Cette fenêtre vous indique que le thread n’a pas de code que le débogueur actif peut afficher. Par exemple, vous pouvez déboguer le code managé, mais le thread est en code natif. La fenêtre propose des suggestions pour résoudre le problème.

**Pour basculer vers un autre thread :**

1. Dans le **Threads** fenêtre, notez l’ID du thread actuel, qui est le thread avec une flèche jaune dans la **Thread actuel** colonne. Vous souhaitez revenir à ce thread de continuer à votre application.

1. Cliquez sur un thread différent et sélectionnez **commutateur à Thread** dans le menu contextuel.

1. Observez que l’emplacement de la flèche jaune a changé dans le **Threads** fenêtre. Le marqueur de thread en cours d’origine reste, sous forme de plan.

   Examinez l’info-bulle sur le marqueur de thread dans l’éditeur de code source et de la liste dans le **Thread** liste déroulante sur le **emplacement de débogage** barre d’outils. Observez que le thread actuel a également été modifié.

1. Sur le **emplacement de débogage** barre d’outils, sélectionnez un thread différent de la **Thread** liste. Notez que le thread actuel change également dans les deux emplacements.

1. Dans l’éditeur de code source, un marqueur de thread avec le bouton droit, pointez sur **commutateur à Thread**, puis sélectionnez un autre thread dans la liste. Observez que le thread actuel change dans les trois emplacements.

Avec le marqueur de thread dans le code source, vous pouvez basculer uniquement vers les threads interrompus à cet emplacement. La fenêtre **Threads** et la barre d’outils **Emplacement de débogage** vous permettent de basculer vers n’importe quel thread.

Vous avez désormais appris les principes fondamentaux du débogage d’applications multithreads. Vous pouvez observer, indicateur et supprimer l’indicateur, Figer et libérer les threads à l’aide de la **Threads** fenêtre, le **Thread** liste dans le **emplacement de débogage** barre d’outils, ou de marqueurs de thread dans le éditeur de code source.

## <a name="see-also"></a>Voir aussi
- [Déboguer les applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Guide pratique pour basculer vers un autre thread pendant un débogage](../debugger/how-to-switch-to-another-thread-while-debugging.md)
