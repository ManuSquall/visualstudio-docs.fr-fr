---
title: Analyser les données d’utilisation de l’UC (ASP.NET Core)
description: Mesurer les performances de l’application dans ASP.NET Core applications à l’aide de l’outil de diagnostic de l’utilisation de l’UC
ms.custom: mvc
ms.date: 02/14/2020
ms.topic: quickstart
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- aspnet
ms.openlocfilehash: aa0c95e3a9f3598cd6399b565adb75faccac22a8
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2021
ms.locfileid: "111761145"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-aspnet-core"></a>Démarrage rapide : analyser les données d’utilisation de l’UC dans Visual Studio (ASP.NET Core)

Visual Studio fournit de nombreuses fonctionnalités puissantes qui vous permettent d’analyser les problèmes de performances dans votre application. Cette rubrique vous offre un moyen rapide de vous familiariser avec quelques-unes des fonctionnalités de base. Ici, nous allons examiner un outil pour identifier les goulots d’étranglement de performances liés à une utilisation élevée de l’UC. Les outils de diagnostics sont pris en charge pour le développement .NET dans Visual Studio (y compris ASP.NET) et pour le développement natif/C++.

Le hub de diagnostic propose de nombreuses autres options pour exécuter et gérer votre session de diagnostic. Si l’outil **Utilisation de l’UC** décrit ici ne vous fournit pas les données dont vous avez besoin, les [autres outils de profilage](../profiling/profiling-feature-tour.md) fournissent des types d’informations différents qui peuvent vous être utiles. Dans de nombreux cas, le goulot d’étranglement des performances de votre application peut ne pas provenir de votre processeur, mais de la mémoire, de l’interface utilisateur de rendu ou du temps de requête réseau. [PerfTips](../profiling/perftips.md), un autre outil de profilage intégré au débogueur, vous permet également d’effectuer un pas à pas détaillé du code et d’identifier le temps nécessaire à l’exécution de fonctions ou de blocs de code particuliers.

Windows 8 et les versions ultérieures sont nécessaires pour exécuter les Outils de profilage avec le débogueur (fenêtre **Outils de diagnostic**). Sur Windows 7 et les versions ultérieures, vous pouvez utiliser l’outil post mortem [Profileur de performances](../profiling/profiling-feature-tour.md).

## <a name="create-a-project"></a>Création d’un projet

1. Ouvrez Visual Studio et créez le projet.

   ::: moniker range="vs-2017"
   Dans la barre de menus supérieure, choisissez **fichier** > **nouveau** > **projet**.

   Dans la boîte de dialogue **nouveau projet** , dans le volet gauche, développez **Visual C#**, puis choisissez **Web**. Dans le volet central, choisissez **ASP.net application Web (.net Core)**. Nommez ensuite le projet *MyProfilingApp_MVC*.

   > [!NOTE]
   > Si vous ne voyez pas le modèle de projet **application Web ASP.net (.net Core)** , choisissez le lien **ouvrir le Visual Studio installer** dans le volet gauche de la boîte de dialogue **nouveau projet** . Visual Studio Installer est lancé. Choisissez la charge de travail **Développement web et ASP.NET**, puis **Modifier**.

   Dans la boîte de dialogue qui s’affiche, choisissez **MVC** dans le volet central, puis cliquez sur **OK**.
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   Dans Visual Studio 2019, choisissez **créer un nouveau projet** dans la fenêtre démarrer. Si la fenêtre démarrer n’est pas ouverte, choisissez  >  **fenêtre démarrer** le fichier, puis **créer un nouveau projet**.

   Tapez **application Web** dans la zone de recherche, choisissez **C#** comme langage, choisissez **ASP.net Core application Web (Model-View-Controller)**, puis cliquez sur **suivant**. Dans l’écran suivant, nommez le projet *MyProfilingApp_MVC*, puis choisissez **suivant**.

   Choisissez le Framework cible recommandé (.NET Core 3,1) ou .NET 5, puis choisissez **créer**.

   > [!NOTE]
   > Si vous ne voyez pas le modèle d' **application Web ASP.net (.net Core)** , vous pouvez l’installer à partir de la fenêtre **créer un nouveau projet** . Dans le **Vous ne trouvez pas ce que vous cherchez ?**, choisissez le lien **Installer plus d’outils et de fonctionnalités**. Ensuite, dans Visual Studio Installer, choisissez la charge de travail **Développement web et ASP.NET**.
   ::: moniker-end

   Visual Studio crée et ouvre votre nouveau projet.

1. Dans Explorateur de solutions, cliquez avec le bouton droit sur le dossier modèles, puis choisissez **Ajouter** une  >  **classe**.

1. Nommez la nouvelle classe `Data.cs` et choisissez **Ajouter**.

1. Dans l’Explorateur de solutions, ouvrez `Models/Data.cs` et ajoutez l’instruction `using` suivante en haut du fichier :

    ```csharp
    using System.Threading;
    ```

1. Dans Data.cs, remplacez le code suivant :

    ```csharp
    public class Data
    {
    }
    ```

    par ce code :

    ```csharp
    public class ServerClass
    {
        const int MIN_ITERATIONS = int.MaxValue / 1000;
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;

        long m_totalIterations = 0;
        readonly object m_totalItersLock = new object();
        // The method that will be called when the thread is started.
        public void GenerateData()
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
        int numberOfThreads = 200;

        public Simple()
        {
            for (int i = 0; i < numberOfThreads; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.GenerateData));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }

        public int GetData()
        {
            // Not returning any meaningful data.
            return numberOfThreads;
        }
    }
    ```

1. Dans l’Explorateur de solutions, ouvrez *Controller/HomeControllers.cs* et remplacez le code suivant :

   ::: moniker range="vs-2017"

    ```csharp
    public ActionResult About()
    {
        ViewBag.Message = "Your application description page.";

        return View();
    }
    ```

    par ce code :

    ```csharp
    public ActionResult About()
    {
        Models.Simple s = new Models.Simple();

        ViewBag.Message = "Your application description page.";

        return View(s.GetData());
    }
    ```

    ::: moniker-end
    ::: moniker range=">=vs-2019"

    ```csharp
    public IActionResult Privacy()
    {
        return View();
    }
    ```

    par ce code :

    ```csharp
    public IActionResult Privacy()
    {
        Models.Simple s = new Models.Simple();

        return View(s.GetData());
    }
    ```

    ::: moniker-end


## <a name="step-1-collect-profiling-data"></a>Étape 1 : Collecter les données de profilage

1. Tout d’abord, définissez un point d’arrêt dans votre application sur cette ligne de code dans le constructeur `Simple` :

    `for (int i = 0; i < 200; i++)`

    Définissez un point d’arrêt en cliquant dans la marge à gauche de la ligne de code.

1. Ensuite, définissez un deuxième point d’arrêt sur l’accolade fermante à la fin du constructeur `Simple` :

     ![Définir des points d’arrêt pour le profilage](../profiling/media/quickstart-cpu-usage-breakpoints-aspnet.png)

    En définissant deux points d’arrêt, vous limitez la collecte de données aux sections de code que vous souhaitez analyser.

1. La fenêtre **Outils de diagnostic** est déjà visible, sauf si vous l’avez désactivée. Pour afficher à nouveau la fenêtre, cliquez sur **Déboguer**  >  **fenêtres**  >  **afficher les outils de diagnostic**.

1. Cliquez sur **Déboguer**  >  **Démarrer le débogage** (ou **Démarrer** dans la barre d’outils, ou **F5**).

1. Une fois le chargement de l’application terminé, cliquez sur le lien approprié en haut de la page Web pour commencer à exécuter le nouveau code.

   ::: moniker range="vs-2017"
   Dans Visual Studio 2017, cliquez sur le lien à **propos** de pour exécuter le code.
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   Dans Visual Studio 2019, cliquez sur le lien **confidentialité** pour exécuter le code.
   ::: moniker-end

1. La vue **Résumé** des outils de diagnostics s’affiche.

1. Pendant que le débogueur est suspendu, activez la collecte des données d’utilisation de l’UC en choisissez **Enregistrer le profil du processeur**, puis ouvrez l’onglet **Utilisation de l’UC**.

     ![Outils de diagnostic - Activer le profilage de l’UC](../profiling/media/quickstart-cpu-usage-summary.png)

     Quand la collecte des données est activée, le bouton d’enregistrement affiche un cercle rouge.

     Quand vous choisissez **Enregistrer le profil du processeur**, Visual Studio commence l’enregistrement de vos fonctions (notamment leur durée d’exécution) et fournit un graphique chronologique qui vous permet de vous concentrer sur des segments spécifiques de la session d’échantillonnage. Vous pouvez afficher ces données collectées uniquement quand votre application est interrompue à un point d’arrêt.

6. Appuyez sur F5 pour exécuter l’application jusqu’au deuxième point d’arrêt.

     Vous disposez maintenant de données de performances pour votre application, et plus spécifiquement pour la région de code qui s’exécute entre les deux points d’arrêt.

     Le profileur commence la préparation des données de thread. Attendez qu’elle se termine.

     L’outil Utilisation de l’UC affiche le rapport sous l’onglet **Utilisation de l’UC**.

     À ce stade, vous pouvez commencer à analyser les données.

## <a name="step-2-analyze-cpu-usage-data"></a>Étape 2 : Analyser les données d’utilisation de l’UC

Nous vous recommandons de commencer à analyser vos données en examinant la liste des fonctions située sous l’onglet Utilisation de l’UC, en identifiant les fonctions qui effectuent la plus grande partie du travail, puis en analysant ces fonctions les unes après les autres.

1. Dans la liste des fonctions, examinez celles qui effectuent le plus de travail.

     ![Outils de diagnostic : onglet Utilisation de l’UC](../profiling/media/quickstart-cpu-usage-cpu-aspnet.png)

    > [!TIP]
    > Les fonctions sont classées par ordre et ce sont celles qui effectuent le plus de travail qui figurent en haut de la liste (elles ne sont pas classées selon leur ordre d’appel). Ainsi, vous pouvez identifier rapidement les fonctions avec les temps d’exécution les plus longs.

2. Dans la liste des fonctions, double-cliquez sur la fonction `MyProfilingApp_MVC.Models.ServerClass::GetNumber`.

    Quand vous double-cliquez sur la fonction, la vue **Appelant/appelé** s’ouvre dans le volet gauche.

    ![Outils de diagnostic : vue Appelant/appelé](../profiling/media/quickstart-cpu-usage-caller-callee-aspnet.png)

    Dans cette vue, la fonction sélectionnée apparaît dans le titre et dans la zone **Fonction active** (ici, `ServerClass::GetNumber`). La fonction qui a appelé la fonction active s’affiche sur la gauche sous **Fonctions appelantes**, et toutes les fonctions appelées par la fonction active s’affichent dans la zone **Fonctions appelées** située à droite. Vous pouvez sélectionner l’une ou l’autre de ces zones pour modifier la fonction active.

    Cette vue montre la durée totale (en ms), ainsi que le pourcentage du temps global d’exécution de l’application, nécessaires à l’exécution de la fonction.

    La section **Corps de la fonction** montre également la durée totale (et le pourcentage correspondant) passée dans le corps de la fonction, à l’exclusion du temps passé dans les fonctions appelantes et appelées. (Dans cette illustration, 2220 ms sur 2235 ont été passées dans le corps de la fonction. Le temps restant (<20 ms) a été passé dans du code externe appelé par cette fonction.) Les valeurs réelles seront différentes, en fonction de votre environnement.

    > [!TIP]
    > Des valeurs élevées dans le **corps de la fonction** peuvent indiquer un goulot d’étranglement de performances au sein de la fonction.

## <a name="next-steps"></a>Étapes suivantes

- [Analyser l’utilisation de la mémoire](../profiling/memory-usage.md) pour identifier les goulots d’étranglement de performances.
- [Analyser l’utilisation de l’UC](../profiling/cpu-usage.md) pour obtenir des informations détaillées sur l’outil d’utilisation de l’UC.
- Analyser l’utilisation de l’UC sans débogueur ou en ciblant une application en cours d’exécution. Pour plus d’informations, consultez la section [Recueillir des données de profilage sans débogage](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) dans [Exécuter des outils de profilage avec ou sans débogueur](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Voir aussi

- [Profilage dans Visual Studio](../profiling/index.yml)
- [Découvrir les outils de profilage](../profiling/profiling-feature-tour.md)
