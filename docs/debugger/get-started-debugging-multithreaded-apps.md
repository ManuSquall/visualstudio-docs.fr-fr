---
title: Apprenez à déboguer les applications multithread
description: Débogage en utilisant les fenêtres Espion parallèle et les piles parallèles dans Visual Studio
ms.custom: H1HackMay2017
ms.date: 11/16/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: 62df746b-b0f6-4df4-83cf-b1d9d2e72833
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 95a198213daa90a1370cba056a8c522495e06c94
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54227978"
---
# <a name="get-started-debugging-multithreaded-applications-c-visual-basic-c"></a>Commencer le débogage d’applications multithread (C#, Visual Basic, C++)
Visual Studio fournit plusieurs outils et les éléments d’interface utilisateur pour vous aider à déboguer les applications multithread. Ce didacticiel montre comment utiliser des marqueurs de thread, le **piles parallèles** fenêtre, le **espion parallèle** fenêtre, points d’arrêt conditionnels et les points d’arrêt de filtre. Pour vous familiariser avec les fonctionnalités de Visual Studio pour déboguer des applications multithreads, ils auront terminé ce didacticiel.

| | |
|---------|---------|
| ![Icône représentant une caméra pour les vidéos](../install/media/video-icon.png "Regarder une vidéo") | [Regardez une vidéo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugging-Multi-threaded-Apps-in-Visual-Studio-2017-MoZPKMD6D_111787171) sur le débogage multithread qui montre des étapes similaires. |

Ces deux rubriques fournissent des informations supplémentaires sur l’utilisation d’autres outils de débogage multithreads :

- Pour utiliser le **emplacement de débogage** barre d’outils et les **Threads** fenêtre, consultez [procédure pas à pas : Déboguer une application multithread](../debugger/how-to-use-the-threads-window.md).

- Pour obtenir un exemple qui utilise <xref:System.Threading.Tasks.Task> (code managé) et le runtime d’accès concurrentiel (C++), consultez [procédure pas à pas : Déboguer une application parallèle Pour les conseils de débogage générales qui s’appliquent aux types d’applications multithreads plus, lisez cette rubrique et celle-ci.
  
Vous devez tout d’abord un projet d’application multithread. Voici un exemple.  
  
## <a name="create-a-multithreaded-app-project"></a>Créer un projet d’application multithread  
  
1.  Dans le menu **Fichier**, sélectionnez **Nouveau** > **Projet**.  
  
     La boîte de dialogue **Nouveau projet** s’affiche.  
  
2.  Sélectionnez une langue **Visual C#** , **Visual C++**, ou **Visual Basic**.  
  
3.  Sous **Windows Desktop**, choisissez **application Console**.  
  
4.  Dans le **nom** , entrez MyThreadWalkthroughApp.  
  
5.  Sélectionnez **OK**.  
  
     Un nouveau projet console s'affiche. Une fois que le projet a été créé, un fichier source s’affiche. Selon le langage que vous avez choisi, le fichier source peut être appelé *Program.cs*, *MyThreadWalkthroughApp.cpp*, ou *Module1.vb*.  
  
6.  Supprimez le code qui s’affiche dans le fichier source et remplacez-le par le code exemple approprié ci-dessous.

    ```csharp
    using System;
    using System.Threading;

    public class ServerClass
    {

        static int count = 0;
        // The method that will be called when the thread is started.
        public void InstanceMethod()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            int data = count++;
            // Pause for a moment to provide a delay to make
            // threads more apparent.
            Thread.Sleep(3000);
            Console.WriteLine(
                "The instance method called by the worker thread has ended.");
        }
    }

    public class Simple
    {
        public static void Main()
        {
            for (int i = 0; i < 10; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.InstanceMethod));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }
    }
    ```

    ```C++
    #include "stdafx.h"
    #include <thread>
    #include <iostream>
    #include <vector>

    using namespace;

    int count = 0;

    void doSomeWork() {

        cout << "The doSomeWork function is running on another thread." << endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        this_thread::sleep_for(chrono::seconds(3));
        cout << "The function called by the worker thread has ended." << endl;
    }

    int main() {
        vector<thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(thread(doSomeWork));
            cout << "The Main() thread calls this after starting the new thread" << endl;
        }

        for (auto& thread : threads) {
            thread.join();
        }

        return 0;
    }
    ```

    ```VB
    Imports System.Threading

    Public Class ServerClass
        ' The method that will be called when the thread is started.
        Public count = 0
        Public Sub InstanceMethod()
            Console.WriteLine(
                    "ServerClass.InstanceMethod is running on another thread.")

            Dim data = count + 1
            ' Pause for a moment to provide a delay to make
            ' threads more apparent.
            Thread.Sleep(3000)
            Console.WriteLine(
                    "The instance method called by the worker thread has ended.")
        End Sub

    End Class

    Public Class Simple

        Public Shared Sub Main()

            Dim ts As New ThreadStarter
            For index = 1 To 10
                ts.CreateThreads()
            Next

        End Sub

    End Class
    Public Class ThreadStarter
        Public Sub CreateThreads()
            Dim serverObject As New ServerClass()

            ' Create the thread object, passing in the
            ' serverObject.InstanceMethod method using a
            ' ThreadStart delegate.
            Dim InstanceCaller As New Thread(AddressOf serverObject.InstanceMethod)

            ' Start the thread.
            InstanceCaller.Start()

            Console.WriteLine("The Main() thread calls this after " _
                        + "starting the new InstanceCaller thread.")

        End Sub
    End Class
    ```
  
7.  Dans le menu **Fichier**, cliquez sur **Enregistrer tout**.  
  
## <a name="debug-the-multithreaded-app"></a>Déboguer l’application multithread  
  
1. Dans l’éditeur de code source, recherchez l’une des extraits de code suivant : 
  
    ```csharp  
    Thread.Sleep(3000);  
    Console.WriteLine();  
    ```  
  
    ```C++  
    this_thread::sleep_for(chrono::seconds(3));
    cout << "The function called by the worker thread has ended." << endl; 
    ```  

    ```VB
    Thread.Sleep(3000)
    Console.WriteLine()
    ```

1. Cliquez dans la marge gauche de la `Thread.Sleep` ou `this_thread::sleep_for` instruction pour insérer un nouveau point d’arrêt.  
  
    Dans la marge, un cercle rouge indique qu’un point d’arrêt est défini à cet emplacement. 
  
2. Sur le **déboguer** menu, sélectionnez **démarrer le débogage** (**F5**).  
  
    Visual Studio génère la solution, l’application commence à s’exécuter avec le débogueur attaché, puis l’application s’arrête au point d’arrêt.  
  
3. Dans l’éditeur de code source, recherchez la ligne qui contient le point d’arrêt.
  
### <a name="ShowThreadsInSource"></a>Découvrir le marqueur de thread  

1.  Dans la barre d’outils Déboguer, sélectionnez le **afficher les Threads dans la Source** bouton ![afficher les Threads dans la Source](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker").

2. Appuyez sur **F11** une fois pour la débogueur une ligne de code d’avance.
  
3.  Examinez la reliure située sur le côté gauche de la fenêtre. Sur cette ligne, vous verrez un *marqueur de thread* icône ![marqueur de Thread](../debugger/media/dbg-thread-marker.png "ThreadMarker") qui ressemble à deux threads tordues. Le marqueur de thread indique qu'un thread est interrompu à cet emplacement.

    Un marqueur de thread peut être partiellement masqué par un point d’arrêt. 
  
4.  Placez le pointeur sur le marqueur de thread. Un DataTip s’affiche vous indiquant le numéro d’identification de nom et le thread pour chaque thread interrompu. Dans ce cas, le nom est probablement `<noname>`. 
  
5.  Sélectionnez le marqueur de thread pour afficher les options disponibles dans le menu contextuel.
    
### <a name="ParallelStacks"></a>Afficher les emplacements de thread

Dans le **piles parallèles** fenêtre, vous pouvez basculer entre une vue Threads et (pour la programmation basée sur les tâches) vue tâches et vous pouvez afficher des informations de pile des appels pour chaque thread. Dans cette application, nous pouvons utiliser la vue Threads.

1. Ouvrez le **piles parallèles** fenêtre en choisissant **déboguer** > **Windows** > **piles parallèles**. Vous devez voir quelque chose de similaire à ce qui suit. Les informations exactes diffèrent selon l’emplacement actuel de chaque thread, votre matériel et votre langage de programmation.

    ![Parallel Stacks Window](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    Dans cet exemple, de gauche à droite nous voir ces informations pour le code managé :
    
    - Le thread principal (côté gauche) a été arrêté sur `Thread.Start`, où le point d’arrêt est indiqué par l’icône de marqueur de thread ![marqueur de Thread](../debugger/media/dbg-thread-marker.png "ThreadMarker").
    - Deux threads ont entré le `ServerClass.InstanceMethod`, un d'entre eux est le thread actuel (flèche jaune), tandis que l’autre thread a cessé dans `Thread.Sleep`.
    - Un nouveau thread (à droite) est également en cours de démarrage, mais est arrêté sur `ThreadHelper.ThreadStart`.

2.  Avec le bouton droit des entrées dans le **piles parallèles** fenêtre pour voir les options disponibles dans le menu contextuel.

    Vous pouvez effectuer différentes actions à partir de ces menus contextuels, mais pour ce didacticiel, nous allons présenter plusieurs de ces détails dans le **espion parallèle** fenêtre (sections suivantes).

    > [!NOTE]
    > Pour afficher une liste des informations sur chaque thread, utilisez la **Threads** fenêtre à la place. Consultez [Procédure pas à pas : Déboguer une Application multithread](../debugger/how-to-use-the-threads-window.md).

### <a name="set-a-watch-on-a-variable"></a>Définir un espion sur une variable

1. Ouvrez le **espion parallèle** en sélectionnant **déboguer** > **Windows** > **espion parallèle**  >  **Espion 1 parallèle**.

2. Sélectionnez la cellule où vous voyez la `<Add Watch>` texte (ou la cellule d’en-tête vide dans la 4e colonne) et entrez `data`.

    Les valeurs de la variable de données pour chaque thread s’affichent dans la fenêtre.

3. Sélectionnez la cellule où vous voyez la `<Add Watch>` texte (ou la cellule d’en-tête vide dans la colonne 5) et entrez `count`.

    Les valeurs pour le `count` variable pour chaque thread s’affichent dans la fenêtre. Si vous ne voyez pas encore autant d’informations, essayez en appuyant sur **F11** plusieurs fois pour passer de l’exécution des threads dans le débogueur.

    ![Parallel Watch Window](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. Avec le bouton droit sur une des lignes dans la fenêtre pour afficher les options disponibles.

### <a name="flag-and-unflag-threads"></a>Ajouter et supprimer des threads  
Vous pouvez signaler des threads pour effectuer le suivi des threads importants et ignorer les autres threads.  
  
1. Dans le **espion parallèle** fenêtre, maintenez la **MAJ** la clé, sélectionnez plusieurs lignes.

2. Avec le bouton droit et sélectionnez **indicateur**.

    Tous les threads sélectionnés sont signalés. Maintenant, vous pouvez filtrer pour afficher uniquement les threads avec indicateur.
  
3.  Dans le **espion parallèle** fenêtre, sélectionnez le **afficher uniquement les Threads avec indicateur** bouton ![afficher les Threads avec indicateur](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker").  
  
    Uniquement les threads avec indicateur s’affichent dans la liste.

    > [!TIP]
    > Une fois que vous avez marqué des threads, vous pouvez cliquez sur une ligne de code dans l’éditeur de code et choisissez **exécuter les Threads avec indicateur au curseur**. Veillez à choisir le code que tous les threads avec indicateur atteindront. Visual Studio va suspendre les threads sur la ligne sélectionnée de code, facilitant ainsi contrôler l’ordre d’exécution par [gel et libération des threads](#bkmk_freeze).

4.  Sélectionnez le **afficher uniquement les Threads avec indicateur** bouton Nouveau pour revenir au **afficher tous les Threads** mode.
    
5. Pour supprimer l’indicateur de threads, cliquez sur un ou plusieurs threads avec indicateur dans le **espion parallèle** fenêtre et sélectionnez **supprimer l’indicateur**.

### <a name="bkmk_freeze"></a> Figer et libérer de l’exécution du thread 

> [!TIP]
> Vous pouvez figer et libérer (suspendre et reprendre) les threads pour contrôler l’ordre dans lequel threads exécutent le travail. Cela peut vous aider à résoudre les problèmes d’accès concurrentiel tels que les interblocages et conditions de concurrence critique.
   
1.  Dans le **espion parallèle** fenêtre, avec toutes les lignes sélectionnées, le bouton droit et sélectionnez **Figer**.

    Dans la deuxième colonne, une icône de pause apparaît pour chaque ligne. L’icône de pause indique que le thread est figé.

2.  Désélectionnez toutes les autres lignes en sélectionnant une ligne uniquement.

3.  Cliquez sur une ligne et sélectionnez **libérer**.

    L’icône de pause disparaît sur cette ligne, indiquant que le thread est figé n’est plus.

4.  Basculez vers l’éditeur de code et appuyez sur **F11**. Seul le thread non figé s’exécute.

    L’application peut également instancier certains nouveaux threads. Les nouveaux threads sont sans indicateur et ne sont pas gelés.

### <a name="bkmk_follow_a_thread"></a> Suivez un thread unique avec des points d’arrêt conditionnels

Il peut être utile de suivre l’exécution d’un thread unique dans le débogueur. Un moyen d’y parvenir consiste à bloquer les threads qui vous n'intéressent pas. Dans certains scénarios, vous devrez peut-être suivre un thread unique sans le figer les autres threads, par exemple pour reproduire un bogue particulier. Pour suivre un thread sans bloquer les autres threads, vous devez éviter d’arrêt dans le code, à l’exception sur le thread qui vous intéresse. Vous pouvez le faire en définissant un [point d’arrêt conditionnel](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).

Vous pouvez définir des points d’arrêt sur les différentes conditions, telles que le nom du thread ou l’ID de thread. Il peut être est utile pour définir la condition sur les données que vous connaissez est unique à chaque thread. Il s’agit d’un scénario de débogage courantes, dans lequel vous êtes plus intéressé par une valeur de données particulière que dans n’importe quel thread particulier.

1. Cliquez sur le point d’arrêt que vous avez créé précédemment et sélectionnez **Conditions**.

2. Dans le **les paramètres de point d’arrêt** fenêtre, entrez `data == 5` pour l’expression conditionnelle.

    ![Point d’arrêt conditionnel](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > Si vous êtes plus intéressé par un thread spécifique, puis utiliser un nom de thread ou un ID de thread pour la condition. Pour ce faire, le **les paramètres de point d’arrêt** fenêtre, sélectionnez **filtre** au lieu de **expression conditionnelle**et suivez les conseils de filtre. Voulez-vous nommer vos threads dans le code de votre application, comme les threads ID modifier lorsque vous redémarrez le débogueur.

3. Fermer le **les paramètres de point d’arrêt** fenêtre.

4. Sélectionnez le redémarrage ![redémarrer une application](../debugger/media/dbg-tour-restart.png "RestartApp") bouton redémarrer votre session de débogage.

    Vous allez vous arrêter dans le code sur le thread où la valeur de la variable de données est 5. Dans le **espion parallèle** fenêtre, recherchez la flèche jaune qui indique le contexte du débogueur actuel.

5. Maintenant, vous pouvez ignorer le code (**F10**) et pas à pas détaillé de code (**F11**) et de suivre l’exécution du thread unique.

    Tant que la condition de point d’arrêt est unique pour le thread, et le débogueur n’appuyez sur n’importe quel autre point d’arrêt sur d’autres threads (vous devrez peut-être désactiver les), vous pouvez ignorer le code et détaillé du code sans basculer vers d’autres threads.

    > [!NOTE]
    > Lorsque vous arrivez le débogueur, tous les threads seront exécutera. Toutefois, le débogueur ne s’arrête dans du code sur d’autres threads, sauf si un des autres threads atteint un point d’arrêt. 
  
## <a name="see-also"></a>Voir aussi  
[Déboguer les applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)  
[Guide pratique pour basculer vers un autre thread pendant un débogage](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
[Guide pratique pour Utiliser la fenêtre Pile parallèles](../debugger/using-the-parallel-stacks-window.md)  
[Guide pratique pour utiliser la fenêtre Espion parallèle](../debugger/how-to-use-the-parallel-watch-window.md)  
