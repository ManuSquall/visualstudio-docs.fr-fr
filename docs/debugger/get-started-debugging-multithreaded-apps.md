---
title: En savoir plus sur le débogage d’applications multithread
description: Débogage à l’aide des fenêtres piles parallèles et espion parallèle dans Visual Studio
ms.custom: ''
ms.date: 02/14/2020
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bc5232d616466ec5aa0916d5d1ad9e7bd5b1247c
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101684115"
---
# <a name="get-started-debugging-multithreaded-applications-c-visual-basic-c"></a>Prise en main du débogage des applications multithread (C#, Visual Basic, C++)

Visual Studio fournit plusieurs outils et éléments d’interface utilisateur pour vous aider à déboguer des applications multithread. Ce didacticiel montre comment utiliser des marqueurs de thread, la fenêtre **Piles parallèles** , la fenêtre **Espion parallèle** , les points d’arrêt conditionnels et les points d’arrêt de filtre. Ce didacticiel vous aidera à vous familiariser avec les fonctionnalités de Visual Studio pour déboguer des applications multithread.

Ces deux rubriques fournissent des informations supplémentaires sur l’utilisation d’autres outils de débogage multithread :

- Pour utiliser la barre d’outils **emplacement de débogage** et la fenêtre **Threads** , consultez [procédure pas à pas : déboguer une application multithread](../debugger/how-to-use-the-threads-window.md).

- Pour obtenir un exemple qui utilise <xref:System.Threading.Tasks.Task> (code managé) et le runtime d’accès concurrentiel (C++), consultez [procédure pas à pas : Déboguer une application parallèle](../debugger/walkthrough-debugging-a-parallel-application.md). Pour obtenir des conseils généraux sur le débogage qui s’appliquent à la plupart des types d’applications multithread, lisez cette rubrique et celle-ci.

Vous avez tout d’abord besoin d’un projet d’application multithread. Un exemple suit.

## <a name="create-a-multithreaded-app-project"></a>Créer un projet d’application multithread

1. Ouvrez Visual Studio et créez un projet.

   ::: moniker range=">=vs-2019"

   Si la fenêtre de démarrage n’est pas ouverte  , choisissez > **fenêtre démarrage** de fichier.

   Dans la fenêtre Démarrer, choisissez **créer un nouveau projet**.

   Dans la fenêtre **Créer un projet**, entrez ou tapez *console* dans la zone de recherche. Ensuite, choisissez **C#**, **C++** ou **Visual Basic** dans la liste langue, puis choisissez **Windows** dans la liste plateforme. 

   Après avoir appliqué les filtres de langue et de plateforme, choisissez le modèle **application console** pour .net Core ou C++, puis choisissez **suivant**.

   > [!NOTE]
   > Si vous ne voyez pas le modèle approprié, accédez à **Outils**  >  **obtenir des outils et des fonctionnalités...**, qui ouvre le Visual Studio installer. Choisissez la charge de travail **développement multiplateforme .net Core** ou **développement bureautique avec C++** , puis choisissez **modifier**.

   Dans la fenêtre **configurer votre nouveau projet** , tapez ou entrez *MyThreadWalkthroughApp* dans la zone **nom du projet** . Ensuite, choisissez **suivant** ou **créer**, quelle que soit l’option disponible.

   Pour un projet .NET Core, choisissez le Framework cible recommandé (.NET Core 3,1) ou .NET 5, puis choisissez **créer**.

   ::: moniker-end
   ::: moniker range="vs-2017"
   Dans la barre de menus supérieure, choisissez **fichier**  >  **nouveau**  >  **projet**. Dans le volet gauche de la boîte de dialogue **nouveau projet** , choisissez ce qui suit :

   - Pour une application C#, sous **Visual c#**, choisissez **Bureau Windows**, puis dans le volet central, choisissez **application console (.NET Framework)**.
   - Pour une application Visual Basic, sous **Visual Basic**, choisissez **Bureau Windows**, puis dans le volet central, choisissez **application console (.NET Framework)**.
   - Pour une application C++, sous **Visual C++**, choisissez **Bureau Windows**,, puis **application console Windows**.

   Si vous ne voyez pas l' **application console (.NET Framework)** pour, pour C++, le modèle de projet d' **application console** , accédez à **Outils**  >  **obtenir des outils et des fonctionnalités...**, qui ouvre le Visual Studio installer. Choisissez la charge de travail **développement de bureau .net** ou **développement bureautique avec C++** , puis choisissez **modifier**.

   Ensuite, tapez un nom tel que *MyThreadWalkthroughApp* , puis cliquez sur **OK**.

   Sélectionnez **OK**.
   ::: moniker-end

   Un nouveau projet console s'affiche. Une fois le projet créé, un fichier source s’affiche. Selon le langage que vous avez choisi, le fichier source peut être appelé *Program.cs*, *MyThreadWalkthroughApp. cpp* ou *Module1. vb*.

1. Supprimez le code qui apparaît dans le fichier source et remplacez-le par l’exemple de code ci-dessous.

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
                "The instance method called by the worker thread has ended. " + data);
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
    // #include "pch.h" // Use with pre-compiled header
    #include <thread>
    #include <iostream>
    #include <vector>
    #include <string>

    int count = 0;

    void doSomeWork() {

        std::cout << "The doSomeWork function is running on another thread." << std::endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        std::this_thread::sleep_for(std::chrono::seconds(3));
        std::string str = std::to_string(data);
        std::cout << "The function called by the worker thread has ended. " + str<< std::endl;
    }

    int main() {
        std::vector<std::thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(std::thread(doSomeWork));
            std::cout << "The Main() thread calls this after starting the new thread" << std::endl;
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
                    "The instance method called by the worker thread has ended. " + data)
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

1. Dans le menu **Fichier**, sélectionnez **Enregistrer tout**.

1. (Visual Basic uniquement) Dans Explorateur de solutions (volet droit), cliquez avec le bouton droit sur le nœud du projet, puis choisissez **Propriétés**. Sous l’onglet **application** , remplacez l' **objet Startup** par **simple**.

## <a name="debug-the-multithreaded-app"></a>Déboguer l’application multithread

1. Dans l’éditeur de code source, recherchez l’un des extraits de code suivants :

    ```csharp
    Thread.Sleep(3000);
    Console.WriteLine();
    ```

    ```C++
    std::this_thread::sleep_for(std::chrono::seconds(3));
    std::cout << "The function called by the worker thread has ended." << std::endl;
    ```

    ```VB
    Thread.Sleep(3000)
    Console.WriteLine()
    ```

1. Cliquez sur la marge gauche de l' `Thread.Sleep` `std::this_thread::sleep_for` instruction ou pour insérer un nouveau point d’arrêt.

    Dans la reliure, un cercle rouge indique qu’un point d’arrêt est défini à cet emplacement.

2. Dans le menu **Déboguer** , sélectionnez **Démarrer le débogage** (**F5**).

    Visual Studio génère la solution, l’application commence à s’exécuter avec le débogueur attaché, puis l’application s’arrête au point d’arrêt.

3. Dans l’éditeur de code source, localisez la ligne qui contient le point d’arrêt.

### <a name="discover-the-thread-marker"></a><a name="ShowThreadsInSource"></a>Détection du marqueur de thread  

1. Dans la barre d’outils déboguer, sélectionnez le bouton **afficher les threads dans la source** ![afficher les threads dans la source](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker").

2. Appuyez une fois sur **F11** pour avancer le débogueur d’une ligne de code.

3. Examinez la reliure située sur le côté gauche de la fenêtre. Sur cette ligne, vous verrez un ![marqueur de thread](../debugger/media/dbg-thread-marker.png "ThreadMarker") icône de *marqueur de thread* qui ressemble à deux threads tordus. Le marqueur de thread indique qu'un thread est interrompu à cet emplacement.

    Un marqueur de thread peut être partiellement masqué par un point d’arrêt.

4. Placez le pointeur sur le marqueur de thread. Un DataTip s’affiche pour vous indiquer le nom et le numéro d’ID de thread pour chaque thread arrêté. Dans ce cas, le nom est probablement `<noname>` .

5. Sélectionnez le marqueur de thread pour afficher les options disponibles dans le menu contextuel.

### <a name="view-the-thread-locations"></a><a name="ParallelStacks"></a>Afficher les emplacements de thread

Dans la fenêtre **Piles parallèles** , vous pouvez basculer entre une vue threads et (pour la programmation basée sur des tâches) et vous pouvez afficher les informations de la pile des appels pour chaque thread. Dans cette application, vous pouvez utiliser la vue threads.

1. Ouvrez la fenêtre **Piles parallèles** en choisissant **Déboguer**  >    >  **Piles parallèles** Windows. Un résultat similaire à ce qui suit doit s’afficher. Les informations exactes diffèrent en fonction de l’emplacement actuel de chaque thread, de votre matériel et de votre langage de programmation.

    ![Fenêtre piles parallèles](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    Dans cet exemple, les informations du code managé sont visibles de gauche à droite.

    - Le thread principal (côté gauche) s’est arrêté le `Thread.Start` , où le point d’arrêt est indiqué par le ![marqueur de thread](../debugger/media/dbg-thread-marker.png "ThreadMarker")de l’icône de marqueur de thread.
    - Deux threads ont entré le `ServerClass.InstanceMethod` , dont l’un est le thread actuel (flèche jaune), tandis que l’autre thread s’est arrêté dans `Thread.Sleep` .
    - Un nouveau thread (à droite) démarre également, mais s’arrête `ThreadHelper.ThreadStart` .

2. Cliquez avec le bouton droit sur entrées dans la fenêtre **Piles parallèles** pour afficher les options disponibles dans le menu contextuel.

    Vous pouvez effectuer diverses actions à partir de ces menus contextuels, mais pour ce didacticiel, nous allons afficher plus de détails dans la fenêtre **Espion parallèle** (sections suivantes).

    > [!NOTE]
    > Pour afficher un affichage de liste avec des informations sur chaque thread, utilisez la fenêtre **Threads** à la place. Consultez [procédure pas à pas : déboguer une application multithread](../debugger/how-to-use-the-threads-window.md).

### <a name="set-a-watch-on-a-variable"></a>Définir un espion sur une variable

1. Ouvrez la fenêtre **Espion parallèle** en sélectionnant **Déboguer**  >  **Windows**  >  **parallèle surveiller**  >  **parallèle espion 1**.

2. Sélectionnez la cellule où vous voyez le `<Add Watch>` texte (ou la cellule d’en-tête vide dans la quatrième colonne) et entrez `data` .

    Les valeurs de la variable de données pour chaque thread s’affichent dans la fenêtre.

3. Sélectionnez la cellule où vous voyez le `<Add Watch>` texte (ou la cellule d’en-tête vide dans la 5e colonne) et entrez `count` .

    Les valeurs de la `count` variable pour chaque thread s’affichent dans la fenêtre. Si vous ne voyez pas encore cette quantité d’informations, essayez d’appuyer sur **F11** plusieurs fois pour avancer l’exécution des threads dans le débogueur.

    ![Fenêtre Espion parallèle](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. Cliquez avec le bouton droit sur l’une des lignes de la fenêtre pour afficher les options disponibles.

### <a name="flag-and-unflag-threads"></a>Ajouter et supprimer des threads
Vous pouvez marquer les threads pour effectuer le suivi des threads importants et ignorer les autres threads.

1. Dans la fenêtre **Espion parallèle** , maintenez la touche **MAJ** enfoncée et sélectionnez plusieurs lignes.

2. Cliquez avec le bouton droit et sélectionnez **indicateur**.

    Tous les threads sélectionnés sont marqués d’un indicateur. À présent, vous pouvez filtrer pour afficher uniquement les threads avec indicateur.

3. Dans la fenêtre **Espion parallèle** , sélectionnez le bouton **afficher uniquement les threads avec** indicateur ![afficher les threads avec indicateur](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker").

    Seuls les threads avec indicateur s’affichent dans la liste.

    > [!TIP]
    > Une fois que vous avez marqué certains threads, vous pouvez cliquer avec le bouton droit sur une ligne de code dans l’éditeur de code et choisir **exécuter les threads avec indicateur sur le curseur**. Veillez à choisir le code auquel tous les threads avec indicateur seront atteints. Visual Studio suspend les threads sur la ligne de code sélectionnée, ce qui facilite le contrôle de l’ordre d’exécution par le [gel et le dégel des threads](#bkmk_freeze).

4. Sélectionnez de nouveau le bouton **afficher uniquement les threads avec indicateur** pour revenir au mode **Afficher tous les threads** .

5. Pour supprimer l’indicateur de threads, cliquez avec le bouton droit sur un ou plusieurs threads avec indicateur dans la fenêtre **Espion parallèle** , puis sélectionnez **Supprimer l’indicateur**.

### <a name="freeze-and-thaw-thread-execution"></a><a name="bkmk_freeze"></a> Figer et libérer l’exécution des threads

> [!TIP]
> Vous pouvez figer et libérer (suspendre et reprendre) les threads pour contrôler l’ordre dans lequel les threads effectuent le travail. Cela peut vous aider à résoudre les problèmes d’accès concurrentiel tels que les blocages et les conditions de concurrence.

1. Dans la fenêtre **Espion parallèle** , avec toutes les lignes sélectionnées, cliquez avec le bouton droit et sélectionnez **figer**.

    Dans la deuxième colonne, une icône de pause s’affiche pour chaque ligne. L’icône de pause indique que le thread est figé.

2. Désélectionnez toutes les autres lignes en sélectionnant une seule ligne.

3. Cliquez avec le bouton droit sur une ligne et sélectionnez **libérer**.

    L’icône de pause disparaît sur cette ligne, indiquant que le thread n’est plus figé.

4. Basculez vers l’éditeur de code et appuyez sur **F11**. Seul le thread non figé s’exécute.

    L’application peut également instancier de nouveaux threads. Les nouveaux threads ne sont pas signalés et ne sont pas figés.

### <a name="follow-a-single-thread-with-conditional-breakpoints"></a><a name="bkmk_follow_a_thread"></a> Suivre un thread unique avec des points d’arrêt conditionnels

Il peut être utile de suivre l’exécution d’un thread unique dans le débogueur. Pour ce faire, vous pouvez figer les threads qui ne vous intéressent pas. Dans certains scénarios, vous devrez peut-être suivre un thread unique sans figer d’autres threads, par exemple pour reproduire un bogue particulier. Pour suivre un thread sans figer d’autres threads, vous devez éviter de vous arrêter dans le code, sauf sur le thread qui vous intéresse. Pour ce faire, vous pouvez définir un [point d’arrêt conditionnel](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).

Vous pouvez définir des points d’arrêt sur différentes conditions, telles que le nom du thread ou l’ID du thread. Il peut être utile de définir la condition sur les données dont vous savez qu’elles sont uniques pour chaque thread. Il s’agit d’un scénario de débogage courant, dans lequel vous êtes plus intéressé par une valeur de données particulière que dans un thread particulier.

1. Cliquez avec le bouton droit sur le point d’arrêt que vous avez créé précédemment et sélectionnez **conditions**.

2. Dans la fenêtre **paramètres de point d’arrêt** , entrez `data == 5` pour l’expression conditionnelle.

    ![Point d’arrêt conditionnel](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > Si vous êtes plus intéressé par un thread spécifique, utilisez un nom de thread ou un ID de thread pour la condition. Pour ce faire, dans la fenêtre **paramètres de point d’arrêt** , sélectionnez **Filtrer** au lieu de l' **expression conditionnelle**, puis suivez les conseils de filtre. Vous souhaiterez peut-être nommer vos threads dans le code de votre application, car les ID des threads changent lorsque vous redémarrez le débogueur.

3. Fermez la fenêtre **paramètres de point d’arrêt** .

4. Sélectionnez le bouton redémarrer l' ![application](../debugger/media/dbg-tour-restart.png "RestartApp") de redémarrage pour redémarrer votre session de débogage.

    Vous allez vous arrêter dans le code du thread où la valeur de la variable de données est 5. Dans la fenêtre **Espion parallèle** , recherchez la flèche jaune indiquant le contexte du débogueur actuel.

5. À présent, vous pouvez effectuer un pas à pas principal dans le code (**F10**) et le code pas à pas détaillé (**F11**) et suivre l’exécution du thread unique.

    Tant que la condition de point d’arrêt est unique pour le thread, et que le débogueur n’atteint aucun autre point d’arrêt sur d’autres threads (vous devrez peut-être les désactiver), vous pouvez effectuer un pas à pas principal dans le code et effectuer un pas à pas détaillé dans le code sans basculer vers d’autres threads.

    > [!NOTE]
    > Lorsque vous avancez le débogueur, tous les threads s’exécutent. Toutefois, le débogueur ne s’arrête pas dans le code d’autres threads, sauf si l’un des autres threads atteint un point d’arrêt.

## <a name="see-also"></a>Voir aussi

- [Déboguer les applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Guide pratique pour basculer vers un autre thread pendant un débogage](../debugger/how-to-switch-to-another-thread-while-debugging.md)
- [Comment : utiliser la fenêtre pile parallèle](../debugger/using-the-parallel-stacks-window.md)
- [Guide pratique pour utiliser la fenêtre Espion parallèle](../debugger/how-to-use-the-parallel-watch-window.md)