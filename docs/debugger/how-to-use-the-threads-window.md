---
title: Déboguer une application multithread
description: Déboguer à l’aide de la fenêtre threads et de la barre d’outils emplacement de débogage dans Visual Studio
ms.date: 02/14/2020
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
ms.openlocfilehash: eb7b7850d8d7582110152d248683f89981933215
ms.sourcegitcommit: 6ef52c2030b37ea7a64fddb32f050ecfb77dd918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416371"
---
# <a name="walkthrough-debug-a-multithreaded-app-using-the-threads-window-c-visual-basic-c"></a>Procédure pas à pas : déboguer une application multithread à l'C#aide de la C++fenêtre threads (, Visual Basic,)

Plusieurs éléments de l’interface utilisateur de Visual Studio vous aident à déboguer des applications multithread. Cet article présente les fonctionnalités de débogage multithread dans la fenêtre de l’éditeur de code, la barre d’outils **emplacement de débogage** et la fenêtre **Threads** . Pour plus d’informations sur les autres outils de débogage des applications multithread, consultez [prise en main du débogage d’applications multithread](../debugger/get-started-debugging-multithreaded-apps.md).

L’exécution de ce didacticiel ne prend que quelques minutes et vous familiarise avec les concepts de base du débogage des applications multithread.

## <a name="create-a-multithreaded-app-project"></a>Créer un projet d’application multithread

Créez le projet d’application multithread suivant à utiliser dans ce didacticiel :

1. Ouvrez Visual Studio et créez un projet.

   ::: moniker range=">=vs-2019"

   Si la fenêtre de démarrage n’est pas ouverte, choisissez **fichier** > **fenêtre démarrer**.

   Dans la fenêtre de démarrage, choisissez **Créer un projet**.

   Dans la fenêtre **Créer un projet**, entrez ou tapez *console* dans la zone de recherche. Ensuite, choisissez **C#** ou **C++** dans la liste langue, puis choisissez **Windows** dans la liste plateforme. 

   Après avoir appliqué les filtres de langue et de plateforme, choisissez l' **application console (.net Core)** ou C++, pour, le modèle d' **application console** , puis choisissez **suivant**.

   > [!NOTE]
   > Si vous ne voyez pas le modèle approprié, accédez à **outils** > **obtenir les outils et fonctionnalités...** , qui ouvre le Visual Studio installer. Choisissez la charge de travail **Développement .NET Desktop** ou **Développement Desktop avec C++** , puis choisissez **Modifier**.

   Dans la fenêtre **configurer votre nouveau projet** , tapez ou entrez *MyThreadWalkthroughApp* dans la zone **nom du projet** . Choisissez ensuite **Créer**.

   ::: moniker-end
   ::: moniker range="vs-2017"
   Dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet**. Dans le volet gauche de la boîte de dialogue **nouveau projet** , choisissez ce qui suit :

   - Pour une C# application, sous **Visual C#** , choisissez **Bureau Windows**, puis dans le volet central, choisissez **application console (.NET Framework)** .
   - Pour une C++ application, sous **Visual C++** , choisissez **Bureau Windows**,, puis **application console Windows**.

   Si vous ne voyez pas **l’application console (.net Core)** ou, C++pour, le modèle de projet d' **application console** , accédez à **Outils** > **obtenir les outils et fonctionnalités...** , qui ouvre le Visual Studio installer. Choisissez la charge de travail **Développement .NET Desktop** ou **Développement Desktop avec C++** , puis choisissez **Modifier**.

   Ensuite, tapez un nom tel que *MyThreadWalkthroughApp* , puis cliquez sur **OK**.

   Sélectionnez **OK**.
   ::: moniker-end

   Un nouveau projet console s'affiche. Une fois le projet créé, un fichier source s’affiche. Selon le langage que vous avez choisi, le fichier source peut être appelé *Program.cs*, *MyThreadWalkthroughApp. cpp*ou *Module1. vb*.

1. Remplacez le code du fichier source par l' C# exemple de C++ code ou de la [prise en main du débogage d’applications multithread](../debugger/get-started-debugging-multithreaded-apps.md).

1. Sélectionnez **Fichier** > **Enregistrer tout**.

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

1. Définissez un point d’arrêt sur la ligne de `Console.WriteLine();` en cliquant dans la marge gauche, ou en sélectionnant la ligne et en appuyant sur **F9**.

   Le point d’arrêt apparaît sous la forme d’un cercle rouge dans la marge gauche, à côté de la ligne de code.

1. Sélectionnez **Déboguer** > **Démarrer le débogage**ou appuyez sur **F5**.

   L’application démarre en mode débogage et s’interrompt au point d’arrêt.

1. En mode arrêt, ouvrez la fenêtre **Threads** en sélectionnant **déboguer** > les **Threads** **Windows** > . Vous devez être dans une session de débogage pour ouvrir ou voir les **Threads** et les autres fenêtres de débogage.

## <a name="examine-thread-markers"></a>Examiner les marqueurs de thread

1. Dans le code source, localisez la ligne de `Console.WriteLine();`.

   1. Cliquez avec le bouton droit dans la fenêtre **Threads** , puis sélectionnez **afficher les threads dans la source** ![afficher les threads dans la source](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") dans le menu.

   La marge à côté de la ligne de code source affiche maintenant un ![marqueur de thread](../debugger/media/dbg-thread-marker.png "Marqueur de thread")icône de *marqueur de thread* . Le marqueur de thread indique qu'un thread est interrompu à cet emplacement. S’il existe plusieurs threads arrêtés à l’emplacement, l’icône ![plusieurs threads](../debugger/media/dbg-multithreaded-show-threads.png "threads multiples") s’affiche.

1. Placez le pointeur sur le marqueur de thread. Un DataTip apparaît, affichant le nom et le numéro d’ID de thread pour le thread ou les threads arrêtés. Les noms de threads peuvent être `<No Name>`.

   >[!TIP]
   >Pour faciliter l’identification des threads sans nom, vous pouvez les renommer dans la fenêtre **Threads** . Cliquez avec le bouton droit sur le thread, puis sélectionnez **Renommer**.

1. Cliquez avec le bouton droit sur le marqueur de thread dans le code source pour afficher les options disponibles dans le menu contextuel.

## <a name="flag-and-unflag-threads"></a>Ajouter et supprimer des threads

Vous pouvez marquer les threads pour effectuer le suivi des threads auxquels vous souhaitez attirer une attention particulière.

Baliser et supprimer les indicateurs de thread à partir de l’éditeur de code source ou de la fenêtre **Threads** . Indiquez si vous souhaitez afficher uniquement les threads avec indicateur, ou tous les threads, à partir des barres d’outils de l' **emplacement de débogage** ou de la fenêtre **Threads** . Les sélections effectuées à partir de n’importe quel emplacement affectent tous les emplacements.

### <a name="flag-and-unflag-threads-in-source-code"></a>Marquer et supprimer les indicateurs de thread dans le code source

1. Ouvrez la barre d’outils **emplacement de débogage** en sélectionnant **Afficher** > **barres d’outils** > **emplacement de débogage**. Vous pouvez également cliquer avec le bouton droit dans la zone de la barre d’outils et sélectionner **emplacement de débogage**.

1. La barre d’outils **emplacement de débogage** comporte trois champs : **processus**, **thread**et **Frame de pile**. Déposez la liste des **Threads** et notez le nombre de threads. Dans la liste des **Threads** , le thread en cours d’exécution est marqué par un symbole de **>** .

1. Dans la fenêtre de code source, placez le curseur sur une icône de marqueur de thread dans la reliure, puis sélectionnez l’icône d’indicateur (ou l’une des icônes d’indicateur vides) dans le DataTip. L’icône d’indicateur devient rouge.

   Vous pouvez également cliquer avec le bouton droit sur une icône de marqueur de thread, pointer sur **indicateur**, puis sélectionner un thread à marquer dans le menu contextuel.

1. Dans la barre d’outils **emplacement de débogage** , sélectionnez l’icône **afficher uniquement les threads avec** indicateur ![afficher les threads avec indicateur](../debugger/media/dbg-threads-show-flagged.png "Afficher les threads avec indicateur"), à droite du champ de **thread** . L’icône est grisée, à moins qu’un ou plusieurs threads soient signalés.

   Seul le thread avec indicateur s’affiche désormais dans la liste déroulante **thread** de la barre d’outils. Pour afficher à nouveau tous les threads, sélectionnez à nouveau l’icône **afficher uniquement les threads avec indicateur** .

   >[!TIP]
   >Une fois que vous avez marqué certains threads, vous pouvez placer votre curseur dans l’éditeur de code, cliquer avec le bouton droit et sélectionner **exécuter les threads avec indicateur sur le curseur**. Veillez à choisir le code auquel tous les threads avec indicateur seront atteints. **Exécuter les threads avec indicateur** sur le curseur interrompt les threads sur la ligne de code sélectionnée, ce qui facilite le contrôle de l’ordre d’exécution par le [gel et le dégel des threads](#bkmk_freeze).

1. Pour activer ou désactiver l’état avec indicateur ou sans indicateur du thread en cours d’exécution, sélectionnez le bouton Activer l’indicateur simple de la barre d’outils **activer l’État marqué du thread actuel** , à gauche du bouton **afficher uniquement les threads avec indicateur** . Le fait de marquer le thread actuel est utile pour localiser le thread actuel lorsque seuls les threads avec indicateur sont affichés.

1. Pour supprimer l’indicateur d’un thread, pointez sur le marqueur de thread dans le code source et sélectionnez l’icône d’indicateur rouge pour le désactiver, ou cliquez avec le bouton droit sur le marqueur de thread et sélectionnez **Supprimer l’indicateur**.

### <a name="flag-and-unflag-threads-in-the-threads-window"></a>Marquer et supprimer les indicateurs de thread dans la fenêtre threads

Dans la fenêtre **Threads** , les threads avec indicateur ont des icônes d’indicateur rouge en regard de celles-ci, tandis que les threads sans indicateur, s’ils sont affichés, ont des icônes vides.

![Threads, fenêtre](../debugger/media/dbg-threads-window.png "Fenêtre Threads")

Sélectionnez une icône d’indicateur pour définir l’état du thread sur marqué ou sans indicateur, en fonction de son état actuel.

Vous pouvez également cliquer avec le bouton droit sur une ligne et sélectionner **marquer, supprimer**l' **indicateur**ou supprimer l' **indicateur de tous les threads** dans le menu contextuel.

La barre d’outils de la fenêtre **Threads** comporte également un bouton **afficher les threads avec indicateur uniquement** , qui est le bouton à droite des deux icônes d’indicateur. Il fonctionne de la même façon que le bouton dans la barre d’outils **emplacement de débogage** , et l’un ou l’autre bouton contrôle l’affichage dans les deux emplacements.

### <a name="other-threads-window-features"></a>Autres fonctionnalités de la fenêtre threads

Dans la fenêtre **Threads** , sélectionnez l’en-tête d’une colonne pour trier les threads par cette colonne. Sélectionnez de nouveau pour inverser l’ordre de tri. Si tous les threads sont affichés, la sélection de la colonne icône d’indicateur trie les threads par État marqué ou sans indicateur.

La deuxième colonne de la fenêtre **Threads** (sans en-tête) est la colonne de **thread actuelle** . Une flèche jaune dans cette colonne marque le point d’exécution actuel.

La colonne **emplacement** indique où chaque thread apparaît dans le code source. Sélectionnez la flèche de développement en regard de l’entrée d' **emplacement** , ou pointez sur l’entrée pour afficher une pile des appels partielle pour ce thread.

>[!TIP]
>Pour obtenir une vue graphique des piles des appels pour les threads, utilisez la fenêtre [Piles parallèles](../debugger/using-the-parallel-stacks-window.md) . Pour ouvrir la fenêtre, pendant le débogage, sélectionnez **Déboguer**> **Piles parallèles** **Windows** > .

En plus des **indicateurs**, des **désindicateurs**et des **désindicateurs tous les threads**, le menu contextuel des éléments de la fenêtre de **thread** contient les éléments suivants :

- Bouton **afficher les threads dans la source** .
- **Affichage hexadécimal**, qui modifie l' **ID de thread**dans la fenêtre **Threads** , du format décimal au format hexadécimal.
- [Basculez vers le thread](#switch-to-another-thread), qui bascule immédiatement l’exécution sur ce thread.
- **Renommer**, qui vous permet de modifier le nom du thread.
- [Figer et libérer des](#bkmk_freeze) commandes.

## <a name="bkmk_freeze"></a>Figer et libérer l’exécution des threads

Vous pouvez figer et libérer, ou suspendre et reprendre, les threads pour contrôler l’ordre dans lequel les threads effectuent le travail. Figer et libérer des threads peut vous aider à résoudre les problèmes d’accès concurrentiel, tels que les blocages et les conditions de concurrence.

> [!TIP]
> Pour suivre un thread unique sans figer d’autres threads, ce qui est également un scénario de débogage courant, consultez [prise en main du débogage d’applications multithread](../debugger/get-started-debugging-multithreaded-apps.md#bkmk_follow_a_thread).

**Pour figer et libérer des threads :**

1. Dans la fenêtre **Threads** , cliquez avec le bouton droit sur n’importe quel thread, puis sélectionnez **figer**. Une icône de **Pause** dans la colonne **thread en cours** indique que le thread est figé.

1. Sélectionnez **colonnes** dans la barre d’outils de la fenêtre **Threads** , puis sélectionnez **nombre d’interruptions** pour afficher la colonne **nombre d’interruptions** . La valeur du compteur suspendu pour le thread figé est **1**.

1. Cliquez avec le bouton droit sur le thread figé, puis sélectionnez **libérer**.

   L’icône de **Pause** disparaît et la valeur du **compteur suspendu** est remplacée par **0**.

## <a name="switch-to-another-thread"></a>Basculer vers un autre thread

Vous pouvez voir que **l’application est en mode arrêt** lorsque vous essayez de basculer vers un autre thread. Cette fenêtre indique que le thread n’a pas de code que le débogueur actuel peut afficher. Par exemple, vous pouvez déboguer du code managé, mais le thread est du code natif. La fenêtre propose des suggestions pour la résolution du problème.

**Pour basculer vers un autre thread :**

1. Dans la fenêtre **Threads** , prenez note de l’ID de thread actuel, qui est le thread avec une flèche jaune dans la colonne de **thread actuelle** . Vous souhaiterez revenir à ce thread pour continuer votre application.

1. Cliquez avec le bouton droit sur un autre thread et sélectionnez **basculer vers le thread** dans le menu contextuel.

1. Notez que l’emplacement de la flèche jaune a été modifié dans la fenêtre **Threads** . Le marqueur de thread actuel d’origine reste également sous forme de plan.

   Examinez l’info-bulle sur le marqueur de thread dans l’éditeur de code source et la liste dans la liste déroulante **thread** de la barre d’outils **emplacement de débogage** . Notez que le thread actuel a également changé.

1. Dans la barre d’outils **emplacement de débogage** , sélectionnez un autre thread dans la liste des **Threads** . Notez que le thread actuel change également dans les deux autres emplacements.

1. Dans l’éditeur de code source, cliquez avec le bouton droit sur un marqueur de thread, pointez sur **basculer vers le thread**, puis sélectionnez un autre thread dans la liste. Notez que le thread actuel est modifié dans les trois emplacements.

Avec le marqueur de thread dans le code source, vous pouvez basculer uniquement vers les threads qui sont arrêtés à cet emplacement. La fenêtre **Threads** et la barre d’outils **Emplacement de débogage** vous permettent de basculer vers n’importe quel thread.

Vous avez maintenant appris les bases du débogage des applications multithread. Vous pouvez observer, marquer et supprimer l’indicateur, et figer et libérer des threads à l’aide de la fenêtre **Threads** , de la liste des **Threads** dans la barre d’outils **emplacement de débogage** ou des marqueurs de thread dans l’éditeur de code source.

## <a name="see-also"></a>Voir aussi
- [Déboguer les applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Guide pratique pour basculer vers un autre thread pendant un débogage](../debugger/how-to-switch-to-another-thread-while-debugging.md)
