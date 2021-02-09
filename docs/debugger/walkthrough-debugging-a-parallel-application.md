---
title: Déboguer une application parallèle | Microsoft Docs
description: Déboguer à l’aide des fenêtres tâches parallèles et piles parallèles dans Visual Studio
ms.date: 02/14/2020
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks walkthrough
- parallel stacks toolwindow
- parallel tasks toolwindow
- parallel applications, debugging [C++]
- debugging, parallel applications
- parallel applications, debugging [Visual Basic]
- parallel applications, debugging [C#]
ms.assetid: 2820ac4c-c893-4d87-8c62-83981d561493
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f46efe377cb01b7b78a9df2de2d1e6fc89826014
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884284"
---
# <a name="walkthrough-debugging-a-parallel-application-in-visual-studio-c-visual-basic-c"></a>Procédure pas à pas : débogage d’une application parallèle dans Visual Studio (C#, Visual Basic, C++)

Cette procédure pas à pas indique comment utiliser les fenêtres **Tâches parallèles** et **Piles parallèles** pour déboguer une application parallèle. Ces fenêtres vous aident à comprendre et à vérifier le comportement au moment de l’exécution du code qui utilise la [bibliothèque parallèle de tâches (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) ou le [Runtime d’accès concurrentiel](/cpp/parallel/concrt/concurrency-runtime). Cette procédure pas à pas fournit un exemple de code qui comporte des points d'arrêt intégrés. Une fois le code arrêté, la procédure pas à pas indique comment utiliser les fenêtres **Tâches parallèles** et **Piles parallèles** pour l’examiner.

 Cette procédure pas à pas aborde les tâches suivantes :

- Comment afficher les piles d'appels de tous les threads dans une vue.

- Comment afficher la liste des instances `System.Threading.Tasks.Task` créées dans votre application.

- Comment afficher les véritables piles d’appels des tâches au lieu des threads.

- Comment accéder au code à partir des fenêtres **Tâches parallèles** et **Piles parallèles**.

- Comment les fenêtres gèrent l'échelle avec les fonctionnalités de regroupement, de zoom et autres.

## <a name="prerequisites"></a>Prérequis
 Cette procédure pas à pas suppose que **uniquement mon code** est activé (il est activé par défaut dans les versions plus récentes de Visual Studio). Dans le menu **Outils**, cliquez sur **Options**, développez le nœud **Débogage**, sélectionnez **Général**, puis **Activer Uniquement mon code (Managé uniquement)**. Si vous ne définissez pas cette fonctionnalité, vous pouvez quand même effectuer cette procédure pas à pas, mais vos résultats peuvent différer de ceux des illustrations.

## <a name="c-sample"></a>Exemple de code C#
 Si vous utilisez l'exemple C#, cette procédure pas à pas suppose également que le code externe est masqué. Pour afficher ou masquer le code externe, cliquez avec le bouton droit sur l’en-tête de table **Nom** de la fenêtre **Pile des appels**, puis activez ou désactivez **Afficher le code externe**. Si vous ne définissez pas cette fonctionnalité, vous pouvez quand même effectuer cette procédure pas à pas, mais vos résultats peuvent différer de ceux des illustrations.

## <a name="c-sample"></a>Exemple C++
 Si vous utilisez l'exemple C++, vous pouvez ignorer les références au code externe de cette rubrique. Le code externe s'applique uniquement à l'exemple C#.

## <a name="illustrations"></a>Illustrations
 Les illustrations de cette rubrique ont été enregistrées sur un ordinateur quadricœur exécutant l'exemple C#. Bien que vous puissiez utiliser d'autres configurations pour effectuer cette procédure pas à pas, les illustrations peuvent différer de celles affichées sur votre ordinateur.

## <a name="creating-the-sample-project"></a>Création de l'exemple de projet
 L'exemple de code de cette procédure pas à pas est relatif à une application qui ne fait rien. L'objectif est simplement de comprendre comment utiliser les fenêtres Outils pour déboguer une application parallèle.

#### <a name="to-create-the-sample-project"></a>Pour créer l'exemple de projet

1. Ouvrez Visual Studio et créez un projet.

   ::: moniker range=">=vs-2019"

   Si la fenêtre de démarrage n’est pas ouverte  , choisissez > **fenêtre démarrage** de fichier.

   Dans la fenêtre Démarrer, choisissez **créer un nouveau projet**.

   Dans la fenêtre **Créer un projet**, entrez ou tapez *console* dans la zone de recherche. Ensuite, choisissez **C#**, **C++** ou **Visual Basic** dans la liste langue, puis choisissez **Windows** dans la liste plateforme. 

   Après avoir appliqué les filtres de langue et de plateforme, choisissez l' **application console (.net Core)** ou, pour C++, le modèle **application console** , puis choisissez **suivant**.

   > [!NOTE]
   > Si vous ne voyez pas le modèle approprié, accédez à **Outils**  >  **obtenir des outils et des fonctionnalités...**, qui ouvre le Visual Studio installer. Choisissez la charge de travail **développement de bureau .net** ou **développement bureautique avec C++** , puis choisissez **modifier**.

   Dans la fenêtre **configurer votre nouveau projet** , tapez un nom ou utilisez le nom par défaut dans la zone **nom du projet** . Ensuite, choisissez **créer**.

   ::: moniker-end
   ::: moniker range="vs-2017"
   Dans la barre de menus supérieure, choisissez **fichier**  >  **nouveau**  >  **projet**. Dans le volet gauche de la boîte de dialogue **nouveau projet** , choisissez ce qui suit :

   - Pour une application C#, sous **Visual c#**, choisissez **Bureau Windows**, puis dans le volet central, choisissez **application console (.NET Framework)**.
   - Pour une application Visual Basic, sous **Visual Basic**, choisissez **Bureau Windows**, puis dans le volet central, choisissez **application console (.NET Framework)**.
   - Pour une application C++, sous **Visual C++**, choisissez **Bureau Windows**,, puis **application console Windows**.

   Si vous ne voyez pas l' **application console (.net Core)** ou, pour C++, le modèle de projet d' **application console** , accédez à **Outils**  >  **obtenir des outils et des fonctionnalités...**, qui ouvre le Visual Studio installer. Choisissez la charge de travail **développement de bureau .net** ou **développement bureautique avec C++** , puis choisissez **modifier**.

   Ensuite, tapez un nom ou utilisez le nom par défaut, puis cliquez sur **OK**.

   Sélectionnez **OK**.
   ::: moniker-end

   Un nouveau projet console s'affiche. Une fois le projet créé, un fichier source s’affiche.

1. Ouvrez le fichier de code .cpp, .cs ou .vb dans le projet. Supprimez son contenu pour créer un fichier de code vide.

1. Collez le code suivant dans le langage choisi dans le fichier de code vide.

   [!code-csharp[Debugger#1](../debugger/codesnippet/CSharp/walkthrough-debugging-a-parallel-application_1.cs)]
   [!code-cpp[Debugger#1](../debugger/codesnippet/CPP/walkthrough-debugging-a-parallel-application_1.cpp)]
   [!code-vb[Debugger#1](../debugger/codesnippet/VisualBasic/walkthrough-debugging-a-parallel-application_1.vb)]

1. Dans le menu **Fichier**, cliquez sur **Enregistrer tout**.

1. Dans le menu **Générer**, cliquez sur **Régénérer la solution**.

    Notez qu'il y a quatre appels à `Debugger.Break` (`DebugBreak` dans l'exemple C++). Vous n'avez donc pas à insérer de points d'arrêt. La simple exécution de l'application entraînera son arrêt dans le débogueur jusqu'à quatre fois.

## <a name="using-the-parallel-stacks-window-threads-view"></a>Utilisation de la fenêtre Piles parallèles : vue Threads
 Dans le menu **Déboguer** , cliquez sur **Démarrer le débogage**. Attendez que le premier point d'arrêt soit atteint.

#### <a name="to-view-the-call-stack-of-a-single-thread"></a>Pour afficher la pile des appels d'un thread unique

1. Dans le menu **Déboguer**, pointez sur **Fenêtres**, puis cliquez sur **Threads**. Ancrez la fenêtre **Threads** en bas de Visual Studio.

2. Dans le menu **Déboguer**, pointez sur **Fenêtres**, puis cliquez sur **Pile des appels**. Ancrez la fenêtre **Pile des appels** en bas de Visual Studio.

3. Double-cliquez sur un thread dans la fenêtre **Threads** pour le rendre actuel. Les threads actuels comportent une flèche jaune. Quand vous modifiez le thread actuel, sa pile des appels est affichée dans la fenêtre **Pile des appels**.

#### <a name="to-examine-the-parallel-stacks-window"></a>Pour examiner la fenêtre Piles parallèles

1. Dans le menu **Déboguer**, pointez sur **Fenêtres**, puis cliquez sur **Piles parallèles**. Assurez-vous que l’option **Threads** est sélectionnée dans la zone située dans l’angle supérieur gauche.

     À l’aide de la fenêtre **Piles parallèles** , vous pouvez afficher plusieurs piles d’appels en même temps dans une seule vue. L’illustration suivante montre la fenêtre **Piles parallèles** au-dessus de la fenêtre **pile des appels** .

     ![Vue Threads dans la fenêtre Piles parallèles](../debugger/media/pdb_walkthrough_1.png "PDB_Walkthrough_1")

     La pile des appels du thread principal s'affiche dans une zone et les piles des appels des quatre autres threads sont regroupées dans une autre zone. Quatre threads sont regroupés car leurs frames de pile partagent les mêmes contextes de méthode, ce qui signifie qu'ils se trouvent dans les mêmes méthodes : `A`, `B` et `C`. Pour afficher les ID de thread et les noms des threads qui partagent la même zone, pointez sur la zone avec l’en-tête (**4 threads**). Le thread actuel est affiché en gras.

     ![Info-bulle affichant les ID de thread et les noms](../debugger/media/pdb_walkthrough_1a.png "PDB_Walkthrough_1A")

     La flèche jaune indique le frame de pile actif du thread actuel.

     Vous pouvez indiquer le détail souhaité pour les frames de pile (**Afficher les noms de modules**, **Afficher les types de paramètre**, **Afficher les noms de paramètres**, **Afficher les valeurs de paramètre**, **Afficher les numéros de ligne** et **Afficher les offsets d’octet**) en cliquant avec le bouton droit dans la fenêtre **Pile des appels**.

     Une surbrillance bleue autour d'une zone indique que le thread actuel fait partie de cette zone. Le thread actuel est également indiqué par le frame de pile en gras dans l'info-bulle. Si vous double-cliquez sur le thread principal dans la fenêtre Threads, vous pouvez observer que la surbrillance bleue dans la fenêtre **Piles parallèles** se déplace en conséquence.

     ![Thread principal mis en surbrillance dans la fenêtre Piles parallèles](../debugger/media/pdb_walkthrough_1c.png "PDB_Walkthrough_1C")

#### <a name="to-resume-execution-until-the-second-breakpoint"></a>Pour continuer l'exécution jusqu'au deuxième point d'arrêt

1. Pour reprendre l’exécution jusqu’au deuxième point d’arrêt, dans le menu **Déboguer**, cliquez sur **Continuer**. L'illustration suivante présente l'arborescence des threads au deuxième point d'arrêt.

     ![Fenêtre Piles parallèles présentant de nombreuses branches](../debugger/media/pdb_walkthrough_2.png "PDB_Walkthrough_2")

     Au premier point d'arrêt, les quatre threads sont tous allés de la méthode S.A à S.B et S.C. Ces informations sont toujours visibles dans la fenêtre **Piles parallèles**, mais les quatre threads ont depuis progressé plus loin. L'un d'entre eux a continué vers S.D, puis S.E. Un autre est allé vers S.F, S.G et S.H. Deux autres ont continué vers S.I et S.J et, de là, l'un d'eux est allé vers S.K et l'autre est parti vers du code externe non-utilisateur.

     Vous pouvez pointer sur l’en-tête de zone, par exemple **1 Thread** ou **2 Threads**, pour afficher les ID des threads. Vous pouvez pointer sur des frames de pile pour afficher les ID des threads et d'autres détails sur les frames. La surbrillance bleue indique le thread actuel et la flèche jaune indique le frame de pile actif du thread actuel.

     L’icône des threads en tissu (lignes intertrames) indique les frames de pile actifs des threads non actuels. Dans la fenêtre **Pile des appels**, double-cliquez sur S.B pour basculer des frames. La fenêtre **Piles parallèles** indique le frame de pile actuel du thread actuel à l’aide d’une icône de flèche incurvée verte.

     Dans la fenêtre **Threads**, basculez entre les threads et remarquez que la vue de la fenêtre **Piles parallèles** est mise à jour.

     Vous pouvez basculer vers un autre thread, ou vers un autre frame d’un autre thread, à l’aide du menu contextuel de la fenêtre **Piles parallèles**. Par exemple, cliquez avec le bouton droit sur S.J, pointez sur **Basculer vers le frame**, puis cliquez sur une commande.

     ![Chemin d’exécution des piles parallèles](../debugger/media/pdb_walkthrough_2b.png "PDB_Walkthrough_2B")

     Cliquez avec le bouton droit sur S.C et pointez sur **Basculer vers le frame**. L'une des commandes comporte une coche qui indique le frame de pile du thread actuel. Vous pouvez basculer vers ce frame du même thread (seule la flèche verte se déplace) ou vous pouvez basculer vers l'autre thread (la surbrillance bleue se déplace également). L'illustration suivante présente le sous-menu.

     ![Menu Piles avec 2 options sur C alors que J est actif](../debugger/media/pdb_walkthrough_3.png "PDB_Walkthrough_3")

     Quand un contexte de méthode est associé à un seul frame de pile, l’en-tête de zone indique **1 Thread** et vous pouvez basculer vers lui en double-cliquant. Si vous double-cliquez sur un contexte de méthode associé à plus d'1 frame, le menu apparaît automatiquement. Lorsque vous pointez sur les contextes de méthode, remarquez le triangle noir à droite. Le fait de cliquer sur ce triangle affiche également le menu contextuel.

     Pour les grandes applications qui comportent de nombreux threads, vous pouvez vous concentrer sur un seul sous-ensemble de threads. La fenêtre **Piles parallèles** peut afficher des piles d’appels uniquement pour les threads avec indicateur. Pour signaler des threads, utilisez le menu contextuel ou la première cellule d'un thread.

     Dans la barre d’outils, cliquez sur le bouton **Afficher uniquement les threads avec indicateur** situé à côté de la zone de liste.

     ![Fenêtre et info-bulle des piles parallèles](../debugger/media/pdb_walkthrough_3a.png "PDB_Walkthrough_3A")

     Désormais, seul le thread avec indicateur s’affiche dans la fenêtre **Piles parallèles** .

#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Pour continuer l'exécution jusqu'au troisième point d'arrêt

1. Pour reprendre l’exécution jusqu’au troisième point d’arrêt, dans le menu **Déboguer**, cliquez sur **Continuer**.

     Lorsque plusieurs threads se trouvent dans la même méthode mais que cette méthode ne figure pas au début de la pile des appels, la méthode s'affiche dans des zones différentes. Un exemple au point d'arrêt actuel est S.L, qui possède trois threads et apparaît dans trois zones. Double-cliquez sur S.L.

     ![Chemin d’exécution dans la fenêtre Piles parallèles](../debugger/media/pdb_walkthrough_3b.png "PDB_Walkthrough_3B")

     Remarquez que S.L apparaît en gras dans les deux autres zones afin que vous puissiez voir où il s'affiche. Si vous souhaitez voir quels frames appeler dans S.L et quels frames sont appelés, cliquez sur le bouton **Basculer dans la vue Méthode** de la barre d’outils. L’illustration suivante montre la vue méthode de la fenêtre **Piles parallèles** .

     ![Vue Méthode dans la fenêtre Piles parallèles](../debugger/media/pdb_walkthrough_4.png "PDW_Walkthrough_4")

     Remarquez comment le diagramme a pivoté sur la méthode sélectionnée et l'a positionnée dans sa propre zone au milieu de la vue. Les appelés et appelants s'affichent en haut et en bas. Cliquez à nouveau sur le bouton **Basculer dans la vue Méthode** pour quitter ce mode.

     Le menu contextuel de la fenêtre **Piles parallèles** comporte également les éléments suivants.

    - **Affichage hexadécimal** bascule les nombres apparaissant dans les info-bulles entre affichage décimal et hexadécimal.

    - Les **paramètres de symbole** ouvrent les boîtes de dialogue respectives.

    - **Afficher les threads dans la source** active ou désactive l’affichage des marqueurs de thread dans votre code source, qui affiche l’emplacement des threads dans votre code source.

    - **Afficher le code externe** affiche tous les frames même s’ils ne figurent pas dans le code utilisateur. Essayez cet élément pour voir le diagramme se développer pour accueillir les frames supplémentaires (qui peuvent être grisés car vous n'avez pas de symboles pour eux).

2. Dans la fenêtre **Piles parallèles**, assurez-vous que le bouton **Défilement automatique vers le frame de pile actif** de la barre d’outils est activé.

     Lorsque vous possédez de grands diagrammes et que vous accédez au point d'arrêt suivant, vous pouvez souhaiter que la vue défile automatiquement vers le frame de pile actif du thread actuel, à savoir le thread qui a atteint en premier le point d'arrêt.

3. Avant de continuer, dans la fenêtre **Piles parallèles**, défilez tout à gauche et tout en bas.

#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Pour continuer l'exécution jusqu'au quatrième point d'arrêt

1. Pour reprendre l’exécution jusqu’au quatrième point d’arrêt, dans le menu **Déboguer**, cliquez sur **Continuer**.

     Remarquez comment la vue défile automatiquement. Basculez des threads dans la fenêtre **Threads** ou basculez des frames de pile dans la fenêtre **Pile des appels**. Notez comment la vue défile toujours automatiquement vers le frame approprié. Désactivez l’option **Défilement automatique vers le frame de pile actif** et notez la différence.

     La **Vue aérienne** est également utile avec les diagrammes de taille importante dans la fenêtre **Piles parallèles**. Par défaut, la **vue oculaire de l’oiseau** est activée. Toutefois, vous pouvez le basculer en cliquant sur le bouton situé entre les barres de défilement dans le coin inférieur droit de la fenêtre, comme indiqué dans l’illustration suivante.

     ![Vue de&#45;œil de l’oiseau dans la fenêtre piles parallèles](../debugger/media/pdb_walkthrough_5.png "PDB_Walkthrough_5")

     Dans la vue d’ensemble de l’oiseau, vous pouvez déplacer le rectangle pour effectuer un panoramique rapide autour du diagramme.

     Une autre façon de déplacer le diagramme consiste à cliquer dans une zone vide de celui-ci et à le faire glisser où vous le souhaitez.

     Pour effectuer un zoom avant ou arrière dans le diagramme, appuyez sur CTRL et maintenez cette touche enfoncée pendant que vous déplacez la roulette de la souris. Vous pouvez également cliquer sur le bouton Zoom de la barre d'outils, puis utiliser l'outil Zoom.

     Vous pouvez également afficher les piles dans le sens haut/bas, plutôt que bas/haut. Pour cela, dans le menu **Outils**, cliquez sur **Options**, puis activez ou désactivez l’option sous le nœud **Débogage**.

2. Avant de continuer, dans le menu **Déboguer**, cliquez sur **Arrêter le débogage** pour arrêter l’exécution.

## <a name="using-the-parallel-tasks-window-and-the-tasks-view-of-the-parallel-stacks-window"></a>Utilisation de la fenêtre Tâches parallèles et de la vue Tâches de la fenêtre Piles parallèles
 Nous vous recommandons d'effectuer les procédures précédentes avant de continuer.

#### <a name="to-restart-the-application-until-the-first-breakpoint-is-hit"></a>Pour redémarrer l'application jusqu'à ce que le premier point d'arrêt soit atteint

1. Dans le menu **Déboguer**, cliquez sur **Démarrer le débogage** et attendez que le premier point d’arrêt soit atteint.

2. Dans le menu **Déboguer**, pointez sur **Fenêtres**, puis cliquez sur **Threads**. Ancrez la fenêtre **Threads** en bas de Visual Studio.

3. Dans le menu **Déboguer**, pointez sur **Fenêtres** et cliquez sur **Pile des appels**. Ancrez la fenêtre **pile des appels** en bas de Visual Studio.

4. Double-cliquez sur un thread dans la fenêtre **Threads** pour le rendre actuel. Les threads actuels comportent une flèche jaune. Lorsque vous modifiez le thread actuel, les autres fenêtres sont mises à jour. Nous allons maintenant examiner les tâches.

5. Dans le menu **Déboguer** , pointez sur **fenêtres**, puis cliquez sur **tâches**. L’illustration suivante montre la fenêtre **tâches** .

     ![Quatre tâches en cours d’exécution dans la fenêtre tâches](../debugger/media/pdb_walkthrough_6.png "PDW_Walkthrough_6")

     Pour chaque tâche en cours, vous pouvez lire l’ID, retourné par la propriété de même nom, l’ID et le nom du thread qui l’exécute, ainsi que son emplacement (le fait de pointer dessus affiche une info-bulle qui comporte l’ensemble de la pile des appels). Sous la colonne **Tâche**, vous pouvez également voir la méthode qui a été passée dans la tâche, en d’autres termes le point de départ.

     Vous pouvez trier toutes les colonnes. Remarquez le glyphe de tri qui indique la colonne et le sens du tri. Vous pouvez également réorganiser les colonnes en les faisant glisser à gauche ou à droite.

     La flèche jaune indique la tâche actuelle. Vous pouvez basculer des tâches en double-cliquant dessus ou en utilisant le menu contextuel. Lorsque vous basculez des tâches, le thread sous-jacent devient le thread actuel et les autres fenêtres sont mises à jour.

     Lorsque vous basculez manuellement d'une tâche à une autre, la flèche jaune se déplace, mais une flèche blanche indique toujours la tâche qui a provoqué l'arrêt du débogueur.

#### <a name="to-resume-execution-until-the-second-breakpoint"></a>Pour continuer l'exécution jusqu'au deuxième point d'arrêt

1. Pour reprendre l’exécution jusqu’au deuxième point d’arrêt, dans le menu **Déboguer**, cliquez sur **Continuer**.

     Auparavant, la colonne **État** indiquait toutes les tâches comme étant actives, mais maintenant deux des tâches sont bloquées. Les tâches peuvent être bloquées pour de nombreuses raisons. Dans la colonne **État**, pointez sur une tâche en attente pour savoir pourquoi elle est bloquée. Par exemple, dans l'illustration suivante, la tâche 3 attend la tâche 4.

     ![Deux tâches en attente dans la fenêtre tâches](../debugger/media/pdb_walkthrough_7.png "PDB_Walkthrough_7")

     La tâche 4, ensuite, attend un gestionnaire possédé par le thread assigné à la tâche 2. (Cliquez avec le bouton droit sur la ligne d’en-tête et choisissez **colonnes**  >  **Assignation de thread** pour afficher la valeur d’affectation de thread pour la tâche 2).

     ![Tâche en attente et info-bulle dans la fenêtre Tâches](../debugger/media/pdb_walkthrough_7a.png "PDB_Walkthrough_7A")

     Vous pouvez marquer une tâche en cliquant sur l’indicateur dans la première colonne de la fenêtre **tâches** .

     Vous pouvez utiliser un indicateur pour effectuer le suivi des tâches entre différents points d’arrêt d’une même session de débogage ou pour filtrer les tâches dont les piles d’appels sont affichées dans la fenêtre **Piles parallèles**.

     Quand vous avez utilisé la fenêtre **Piles parallèles** auparavant, vous avez affiché les threads d’application. Affichez à nouveau la fenêtre **Piles parallèles** mais, cette fois, visualisez les tâches d’application. Pour cela, sélectionnez **Tâches** dans la zone dans l’angle supérieur gauche. L’illustration suivante présente la vue Tâches.

     ![Vue Tâches dans la fenêtre Piles parallèles](../debugger/media/pdb_walkthrough_8.png "PDB_Walkthrough_8")

     Les threads qui n’exécutent actuellement pas de tâches n’apparaissent pas dans la vue Tâches de la fenêtre **Piles parallèles**. En outre, pour les threads qui exécutent des tâches, certains des frames de pile qui ne sont pas associés aux tâches sont filtrés à partir du haut et bas de la pile.

     Affichez à nouveau la fenêtre **tâches** . Cliquez avec le bouton droit sur un en-tête de colonne pour afficher un menu contextuel pour cette colonne.

     Vous pouvez utiliser le menu contextuel pour ajouter ou supprimer des colonnes. Par exemple, la colonne AppDomain n'est pas sélectionnée. Elle ne s'affiche donc pas dans la liste. Cliquez sur **Parent**. La colonne **Parent** s’affiche sans valeur pour chacune des quatre tâches.

#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Pour continuer l'exécution jusqu'au troisième point d'arrêt

1. Pour reprendre l’exécution jusqu’au troisième point d’arrêt, dans le menu **Déboguer**, cliquez sur **Continuer**.

     Une nouvelle tâche, la tâche 5, est en cours d’exécution et la tâche 4 est maintenant en attente. Vous pouvez voir pourquoi en pointant sur la tâche en attente dans la fenêtre **État**. Dans la colonne **parent** , Notez que la tâche 4 est le parent de la tâche 5.

     Pour mieux visualiser la relation parent-enfant, cliquez avec le bouton droit sur la ligne d’en-tête de colonne, puis cliquez sur **vue parent enfant**. L'illustration suivante doit apparaître.

     ![Vue enfant&#45;parent dans la fenêtre tâches](../debugger/media/pdb_walkthrough_9.png "PDB_Walkthrough_9")

     Notez que la tâche 4 et la tâche 5 s’exécutent sur le même thread (Affichez la colonne d' **affectation de thread** si elle est masquée). Ces informations ne s’affichent pas dans la fenêtre **Threads** . le voir ici est un autre avantage de la fenêtre **tâches** . Pour confirmer ceci, affichez la fenêtre **Piles parallèles**. Veillez à bien voir **Tâches**. Localisez les tâches 4 et 5 en double-cliquant dessus dans la fenêtre **tâches** . La surbrillance bleue de la fenêtre **Piles parallèles** est alors mise à jour. Vous pouvez également localiser les tâches 4 et 5 en analysant les info-bulles de la fenêtre **Piles parallèles**.

     ![Vue Tâche dans la fenêtre Piles parallèles](../debugger/media/pdb_walkthrough_9a.png "PDB_Walkthrough_9A")

     Dans la fenêtre **Piles parallèles**, cliquez avec le bouton droit sur S.P, puis cliquez sur **Atteindre le thread**. La fenêtre passe à la vue Threads et le frame correspondant s'affiche. Vous pouvez voir les deux tâches sur le même thread.

     ![Thread mis en surbrillance dans la vue Threads](../debugger/media/pdb_walkthrough_9b.png "PDB_Walkthrough_9B")

     Ceci est un autre avantage de la vue Tâches de la fenêtre **Piles parallèles** par rapport à la fenêtre **Threads**.

#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Pour continuer l'exécution jusqu'au quatrième point d'arrêt

1. Pour reprendre l’exécution jusqu’au troisième point d’arrêt, dans le menu **Déboguer**, cliquez sur **Continuer**. Cliquez sur l’en-tête de colonne **ID** pour trier par ID. L'illustration suivante doit apparaître.

     ![Les 4 états de tâche dans la fenêtre Piles parallèles](../debugger/media/pdb_walkthrough_10.png "PDB_Walkthrough_10")

     Étant donné que la tâche 5 est terminée, elle n’est plus affichée. Si ce n’est pas le cas sur votre ordinateur et que le blocage n’est pas affiché, vous devez effectuer un pas à pas détaillé en appuyant sur **F11**.

     La tâche 3 et la tâche 4 sont maintenant en attente les unes des autres et sont bloquées. Il y a également 5 nouvelles tâches qui sont des enfants de la tâche 2 et qui sont maintenant planifiées. Les tâches planifiées sont des tâches qui ont été démarrées dans le code mais qui n'ont pas encore été exécutées. Par conséquent, leurs colonnes **Emplacement** et **Affectation de thread** sont vides.

     Ouvrez à nouveau la fenêtre **Piles parallèles**. L'en-tête de chaque zone comporte une info-bulle qui affiche les ID et noms de thread. Basculez en vue Tâches dans la fenêtre **Piles parallèles**. Pointez sur un en-tête pour afficher l'ID et le nom de la tâche, ainsi que son état, comme indiqué dans l'illustration suivante.

     ![Info-bulle d'en-tête dans la fenêtre Piles parallèles](../debugger/media/pdb_walkthrough_11.png "PDB_Walkthrough_11")

     Vous pouvez regrouper les tâches par colonne. Dans la fenêtre **tâches** , cliquez avec le bouton droit sur l’en-tête de colonne **État** , puis cliquez sur **Grouper par État**. L’illustration suivante montre la fenêtre **tâches** regroupée par État.

     ![Tâches groupées dans la fenêtre tâches](../debugger/media/pdb_walkthrough_12.png "PDB_Walkthrough_12")

     Vous pouvez également regrouper les tâches en fonction d'une autre colonne. Cela vous permet de vous concentrer sur un sous-ensemble de tâches. Chaque groupe réductible comporte un certain nombre des éléments regroupés ensemble.

     La dernière fonctionnalité de la fenêtre **tâches** à examiner est le menu contextuel qui s’affiche lorsque vous cliquez avec le bouton droit sur une tâche.

     Ce menu contextuel contient différentes commandes en fonction de l’état de la tâche. Ces commandes sont **Copier**, **Sélectionner tout**, **Affichage hexadécimal**, **Basculer vers la tâche**, **Verrouiller le thread affecté**, **Verrouiller tous les threads sauf celui-ci**, **Libérer le thread affecté** et **Marquer**.

     Vous pouvez verrouiller le thread sous-jacent d'une ou plusieurs tâches, ainsi que verrouiller tous les threads sauf celui qui est assigné. Un thread figé est représenté dans la fenêtre **tâches** comme il le fait dans la fenêtre **Threads** , par une icône de *Pause* bleue.

## <a name="summary"></a>Résumé
 Cette procédure pas à pas a présenté les fenêtres de débogage **Tâches parallèles** et **Piles parallèles**. Vous pouvez utiliser ces fenêtres sur de véritables projets qui utilisent du code multithread. Vous pouvez examiner le code parallèle rédigé en C++, C# ou Visual Basic.

## <a name="see-also"></a>Voir aussi
- [Débogage d’applications multithread](../debugger/walkthrough-debugging-a-parallel-application.md)
- [Présentation du débogueur](../debugger/debugger-feature-tour.md)
- [Débogage du code managé](../debugger/debugging-managed-code.md)
- [Programmation parallèle](/dotnet/standard/parallel-programming/index)
- [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime)
- [Utilisation de la fenêtre Piles parallèles](../debugger/using-the-parallel-stacks-window.md)
- [Utilisation de la fenêtre Tâches](../debugger/using-the-tasks-window.md)
