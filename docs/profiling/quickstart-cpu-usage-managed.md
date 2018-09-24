---
title: Analyser les données d’utilisation de l’UC (code managé)
description: Mesurer les performances des applications en C# et Visual Basic à l’aide de l’outil de diagnostic de l’utilisation de l’UC
ms.custom: mvc
ms.date: 08/06/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 35c6fd1ea079dd95367bcb7763787f0b06839ecb
ms.sourcegitcommit: db94ca7a621879f98d4c6aeefd5e27da1091a742
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2018
ms.locfileid: "42626780"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-managed-code"></a>Démarrage rapide : analyser les données d’utilisation de l’UC dans Visual Studio (code managé)

Visual Studio fournit de nombreuses fonctionnalités puissantes qui vous permettent d’analyser les problèmes de performances dans votre application. Cette rubrique vous offre un moyen rapide de vous familiariser avec quelques-unes des fonctionnalités de base. Ici, nous allons examiner l’outil pour identifier les goulots d’étranglement de performances liés à une utilisation élevée de l’UC. Les outils de diagnostics sont pris en charge pour le développement .NET dans Visual Studio (y compris ASP.NET) et pour le développement natif/C++.

Le hub de diagnostic propose de nombreuses autres options pour exécuter et gérer votre session de diagnostic. Si l’outil **Utilisation de l’UC** décrit ici ne vous fournit pas les données dont vous avez besoin, les [autres outils de profilage](../profiling/profiling-feature-tour.md) fournissent d’autres types d’informations qui peuvent vous être utiles. Dans de nombreux cas, le goulot d’étranglement des performances de votre application peut ne pas provenir de votre processeur, mais de la mémoire, de l’interface utilisateur de rendu ou du temps de requête réseau. Le hub de diagnostic vous offre de nombreuses autres options pour enregistrer et analyser ce type de données.

Windows 8 et les versions ultérieures sont nécessaires pour exécuter les Outils de profilage avec le débogueur (fenêtre **Outils de diagnostic**). Sur Windows 7 et les versions ultérieures, vous pouvez utiliser l’outil post mortem [Profileur de performances](../profiling/profiling-feature-tour.md).

## <a name="create-a-project"></a>Créer un projet

1. Dans Visual Studio, sélectionnez **Fichier** > **Nouveau projet**.

2. Sous **Visual C#** ou **Visual Basic**, choisissez **Windows Desktop** puis, dans le volet central, choisissez **Application console (.NET Framework)**.

    Si vous ne voyez pas le modèle de projet **Application console**, cliquez sur le lien **Ouvrir Visual Studio Installer** dans le volet gauche de la boîte de dialogue **Nouveau projet**. Visual Studio Installer est lancé. Choisissez la charge de travail **Développement .NET Desktop**, puis choisissez **Modifier**.

3. Tapez un nom tel que **MyProfilerApp** et cliquez sur **OK**.

    Visual Studio crée le projet.

2. Ouvrez le fichier *Program.cs* et remplacez tout le code par le code suivant :

    ```csharp
    using System;
    using System.Threading;
    public class ServerClass
    {
        const int MIN_ITERATIONS = int.MaxValue / 1000;
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;

        long m_totalIterations = 0;
        readonly object m_totalItersLock = new object();
        // The method that will be called when the thread is started.
        public void DoWork()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            var x = GetNumber();
        }

        private int GetNumber()
        {
            var rand = new Random();
            var iters = rand.Next(MIN_ITERATIONS, MAX_ITERATIONS);
            var result = 0;
            lock (m_totalItersLock)
            {
                m_totalIterations += iters;
            }
            // we're just spinning here
            // and using Random to frustrate compiler optimizations
            for (var i = 0; i < iters; i++)
            {
                result = rand.Next();
            }
            return result;
        }
    }

    public class Simple
    {
        public static void Main()
        {
            for (int i = 0; i < 200; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.DoWork));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }
    }
    ```

    ```vb
    Imports System
    Imports System.Threading

    Namespace MyProfilerApp
        Public Class ServerClass
            Const MIN_ITERATIONS As Integer = Integer.MaxValue / 1000
            Const MAX_ITERATIONS As Integer = MIN_ITERATIONS + 10000

            Private m_totalIterations As Long = 0
            ReadOnly m_totalItersLock As New Object()
            ' The method that will be called when the thread is started.
            Public Sub DoWork()
                Console.WriteLine("ServerClass.InstanceMethod is running on another thread.")

                Dim x = GetNumber()
            End Sub

            Private Function GetNumber() As Integer
                Dim rand = New Random()
                Dim iters = rand.[Next](MIN_ITERATIONS, MAX_ITERATIONS)
                Dim result = 0
                SyncLock m_totalItersLock
                    m_totalIterations += iters
                End SyncLock
                ' we're just spinning here
                ' and using Random to frustrate compiler optimizations
                For i As Integer = 0 To iters - 1
                    result = rand.[Next]()
                Next
                Return result
            End Function
        End Class

        Public Class Simple
            Public Shared Sub Main()
                For i As Integer = 0 To 199
                    CreateThreads()
                Next
            End Sub
            Public Shared Sub CreateThreads()
                Dim serverObject As New ServerClass()

                Dim InstanceCaller As New Thread(New ThreadStart(AddressOf serverObject.DoWork))
                ' Start the thread.
                InstanceCaller.Start()

                Console.WriteLine("The Main() thread calls this after " + "starting the new InstanceCaller thread.")

            End Sub
        End Class
    End Namespace
    ```

    > [!NOTE]
    > En Visual Basic, vérifiez que l’objet de démarrage est défini sur `Sub Main` (**Propriétés** > **Applications** > **Objet de démarrage**).

##  <a name="step-1-collect-profiling-data"></a>Étape 1 : Collecter les données de profilage

1.  Tout d’abord, définissez un point d’arrêt dans votre application sur cette ligne de code dans la fonction `Main` :

    `for (int i = 0; i < 200; i++)`

    ou, pour Visual Basic :

    `For i As Integer = 0 To 199`

    Définissez un point d’arrêt en cliquant dans la marge à gauche de la ligne de code.

2.  Ensuite, définissez un deuxième point d’arrêt sur l’accolade fermante à la fin de la fonction `Main` :

     ![Définir des points d’arrêt pour le profilage](../profiling/media/quickstart-cpu-usage-breakpoints.png "Définir des points d’arrêt pour le profilage")

    > [!TIP]
    > En définissant deux points d’arrêt, vous limitez la collecte de données aux sections de code que vous souhaitez analyser.

3.  La fenêtre **Outils de diagnostic** est déjà visible, sauf si vous l’avez désactivée. Pour réafficher la fenêtre, cliquez sur **Déboguer** > **Fenêtres** > **Afficher les outils de diagnostic**.

4.  Cliquez sur **Déboguer** > **Démarrer le débogage** (ou bien sur **Démarrer** dans la barre d’outils, ou sur **F5**).

     Quand l’application est chargée, la vue **Résumé** des outils de diagnostics s’affiche.

5.  Pendant que le débogueur est suspendu, activez la collecte des données d’utilisation de l’UC en choisissez **Enregistrer le profil du processeur**, puis ouvrez l’onglet **Utilisation de l’UC**.

     ![Activation du profilage de l’UC dans les outils de diagnostic](../profiling/media/quickstart-cpu-usage-summary.png "Activation du profilage de l’UC dans les outils de diagnostic")

     Quand la collecte des données est activée, le bouton d’enregistrement affiche un cercle rouge.

     Quand vous choisissez **Enregistrer le profil du processeur**, Visual Studio commence l’enregistrement de vos fonctions (notamment leur durée d’exécution) et fournit un graphique chronologique qui vous permet de vous concentrer sur des segments spécifiques de la session d’échantillonnage. Vous pouvez afficher ces données collectées uniquement quand votre application est interrompue à un point d’arrêt.

6.  Appuyez sur **F5** pour exécuter l’application jusqu’au deuxième point d’arrêt.

     Vous disposez maintenant de données de performances pour votre application, et plus spécifiquement pour la région de code qui s’exécute entre les deux points d’arrêt.

     Le profileur commence la préparation des données de thread. Attendez qu’elle se termine.

     L’outil Utilisation de l’UC affiche le rapport sous l’onglet **Utilisation de l’UC**.

     À ce stade, vous pouvez commencer à analyser les données.

## <a name="step-2-analyze-cpu-usage-data"></a>Étape 2 : Analyser les données d’utilisation de l’UC

Nous vous recommandons de commencer à analyser vos données en examinant la liste des fonctions située sous l’onglet Utilisation de l’UC, en identifiant les fonctions qui effectuent la plus grande partie du travail, puis en analysant ces fonctions les unes après les autres.

1. Dans la liste des fonctions, examinez celles qui effectuent le plus de travail.

     ![Outils de diagnostics - Onglet Utilisation de l’UC](../profiling/media/quickstart-cpu-usage-cpu.png "DiagToolsCPUUsageTab")

    > [!TIP]
    > Les fonctions sont classées par ordre et ce sont celles qui effectuent le plus de travail qui figurent en haut de la liste (elles ne sont pas classées selon leur ordre d’appel). Ainsi, vous pouvez identifier rapidement les fonctions avec les temps d’exécution les plus longs.

2. Dans la liste des fonctions, double-cliquez sur la fonction `ServerClass::GetNumber`.

    Quand vous double-cliquez sur la fonction, la vue **Appelant/appelé** s’ouvre dans le volet gauche.

    ![Outils de diagnostics - Vue Appelant/appelé](../profiling/media/quickstart-cpu-usage-caller-callee.png "DiagToolsCallerCallee")

    Dans cette vue, la fonction sélectionnée apparaît dans le titre et dans la zone **Fonction active** (ici, `GetNumber`). La fonction qui a appelé la fonction active s’affiche sur la gauche sous **Fonctions appelantes**, et toutes les fonctions appelées par la fonction active s’affichent dans la zone **Fonctions appelées** située à droite. Vous pouvez sélectionner l’une ou l’autre de ces zones pour modifier la fonction active.

    Cette vue montre la durée totale (en ms), ainsi que le pourcentage du temps global d’exécution de l’application, nécessaires à l’exécution de la fonction.

    La section **Corps de la fonction** montre également la durée totale (et le pourcentage correspondant) passée dans le corps de la fonction, à l’exclusion du temps passé dans les fonctions appelantes et appelées. (Dans cette illustration, 2856 ms sur 2863 ont été passées dans le corps de la fonction. Le temps restant (<20 ms) a été passé dans du code externe appelé par cette fonction.) Les valeurs réelles seront différentes, en fonction de votre environnement.

    > [!TIP]
    > Des valeurs élevées dans le **corps de la fonction** peuvent indiquer un goulot d’étranglement de performances au sein de la fonction.

## <a name="next-steps"></a>Étapes suivantes

- [Analyser l’utilisation de la mémoire](../profiling/memory-usage.md) pour identifier les goulots d’étranglement de performances.
- [Analyser l’utilisation de l’UC](../profiling/cpu-usage.md) pour obtenir des informations détaillées sur l’outil d’utilisation de l’UC.
- Analyser l’utilisation de l’UC sans débogueur ou en ciblant une application en cours d’exécution. Pour plus d’informations, consultez la section [Recueillir des données de profilage sans débogage](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) dans [Exécuter des outils de profilage avec ou sans débogueur](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Voir aussi

- [Profilage dans Visual Studio](../profiling/index.md)
- [Découvrir les outils de profilage](../profiling/profiling-feature-tour.md)