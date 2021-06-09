---
title: Analyser les données d’utilisation de l’UC (C++)
description: Mesurer les performances des applications en C++ à l’aide de l’outil de diagnostic de l’utilisation de l’UC
ms.date: 02/14/2020
ms.topic: quickstart
f1_keywords:
- ''
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 8c68cc67d768dbe2b1c42671a02360e5cef2b56b
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760937"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-c"></a>Démarrage rapide : analyser les données d’utilisation de l’UC dans Visual Studio (C++)

Visual Studio fournit de nombreuses fonctionnalités puissantes qui vous permettent d’analyser les problèmes de performances dans votre application. Cette rubrique vous offre un moyen rapide de vous familiariser avec quelques-unes des fonctionnalités de base. Ici, nous allons examiner l’outil pour identifier les goulots d’étranglement de performances liés à une utilisation élevée de l’UC. Les outils de diagnostics sont pris en charge pour le développement .NET dans Visual Studio (y compris ASP.NET) et pour le développement natif/C++.

Le hub de diagnostic propose de nombreuses autres options pour exécuter et gérer votre session de diagnostic. Si l’outil **Utilisation de l’UC** décrit ici ne vous fournit pas les données dont vous avez besoin, les [autres outils de profilage](../profiling/profiling-feature-tour.md) fournissent des types d’informations différents qui peuvent vous être utiles. Dans de nombreux cas, le goulot d’étranglement des performances de votre application peut ne pas provenir de votre processeur, mais de la mémoire, de l’interface utilisateur de rendu ou du temps de requête réseau. Le profileur de performances vous offre de nombreuses autres options pour enregistrer et analyser ce type de données. [PerfTips](../profiling/perftips.md), un autre outil de profilage intégré au débogueur, vous permet également d’effectuer un pas à pas détaillé du code et d’identifier le temps nécessaire à l’exécution de fonctions ou de blocs de code particuliers.

Windows 8 et les versions ultérieures sont nécessaires pour exécuter les Outils de profilage avec le débogueur (fenêtre **Outils de diagnostic**). Sur Windows 7 et les versions ultérieures, vous pouvez utiliser l’outil post mortem [Profileur de performances](../profiling/profiling-feature-tour.md).

## <a name="create-a-project"></a>Création d’un projet

1. Ouvrez Visual Studio et créez le projet.

   ::: moniker range="vs-2017"
   Dans la barre de menus supérieure, choisissez **fichier** > **nouveau** > **projet**.

   Dans la boîte de dialogue **nouveau projet** dans le volet gauche, développez **Visual C++**, puis choisissez **Bureau Windows**. Dans le volet central, choisissez **application console Windows**. Nommez ensuite le projet *Diagnostics_Get_Started_Native*.

   Si vous ne voyez pas le modèle de projet d' **application console Windows** , choisissez le lien **ouvrir le Visual Studio installer** dans le volet gauche de la boîte de dialogue **nouveau projet** . Visual Studio Installer est lancé. Choisissez la charge **de travail développement Desktop en C++** , puis choisissez **modifier**.
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   Si la fenêtre de démarrage n’est pas ouverte  , choisissez > **fenêtre démarrage** de fichier.

   Dans la fenêtre Démarrer, choisissez **créer un nouveau projet**.

   Dans la fenêtre **Créer un projet**, entrez ou tapez *console* dans la zone de recherche. Ensuite, choisissez **C++** dans la liste langue, puis choisissez **Windows** dans la liste plateforme.

   Après avoir appliqué les filtres de langue et de plateforme, choisissez le modèle **application console** , puis cliquez sur **suivant**.

   > [!NOTE]
   > Si vous ne voyez pas le modèle d' **application console** , vous pouvez l’installer à partir de la fenêtre **créer un nouveau projet** . Dans le **Vous ne trouvez pas ce que vous cherchez ?**, choisissez le lien **Installer plus d’outils et de fonctionnalités**. Ensuite, dans la Visual Studio Installer, choisissez la charge de travail **développement Desktop en C++** .

   Dans la fenêtre **configurer votre nouveau projet** , tapez ou entrez *Diagnostics_Get_Started_Native* dans la zone **nom du projet** . Ensuite, choisissez **créer**.

   ::: moniker-end

   Visual Studio ouvre votre nouveau projet.

1. Dans *Diagnostics_Get_Started_Native*, remplacez le code suivant

    ```c++
    int main()
    {
        return 0;
    }
    ```

    par ce code (ne supprimez pas `#include "stdafx.h"`) :

    ```c++
    #include <iostream>
    #include <limits>
    #include <mutex>
    #include <random>
    #include <functional>

    //.cpp file code:

    static constexpr int MIN_ITERATIONS = std::numeric_limits<int>::max() / 1000;
    static constexpr int MAX_ITERATIONS = MIN_ITERATIONS + 10000;

    long long m_totalIterations = 0;
    std::mutex m_totalItersLock;

    int getNumber()
    {

        std::uniform_int_distribution<int> num_distribution(MIN_ITERATIONS, MAX_ITERATIONS);
        std::mt19937 random_number_engine; // pseudorandom number generator
        auto get_num = std::bind(num_distribution, random_number_engine);
        int random_num = get_num();

        auto result = 0;
        {
            std::lock_guard<std::mutex> lock(m_totalItersLock);
            m_totalIterations += random_num;
        }
        // we're just spinning here
        // to increase CPU usage
        for (int i = 0; i < random_num; i++)
        {
            result = get_num();
        }
        return result;
    }

    void doWork()
    {
        std::wcout << L"The doWork function is running on another thread." << std::endl;

        auto x = getNumber();
    }

    int main()
    {
        std::vector<std::thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(std::thread(doWork));
            std::cout << "The Main() thread calls this after starting the new thread" << std::endl;
        }

        for (auto& thread : threads) {
            thread.join();
        }

        return 0;
    }
    ```

## <a name="step-1-collect-profiling-data"></a>Étape 1 : Collecter les données de profilage

1. Tout d’abord, définissez un point d’arrêt dans votre application sur cette ligne de code dans la fonction `main` :

    `for (int i = 0; i < 10; ++i) {`

    Définissez un point d’arrêt en cliquant dans la marge à gauche de la ligne de code.

2. Ensuite, définissez un deuxième point d’arrêt sur l’accolade fermante à la fin de la fonction `main` :

     ![Définir des points d’arrêt pour le profilage](../profiling/media/quickstart-cpu-usage-breakpoints-cplusplus.png "Définir des points d’arrêt pour le profilage")

    En définissant deux points d’arrêt, vous limitez la collecte de données aux sections de code que vous souhaitez analyser.

3. La fenêtre **Outils de diagnostic** est déjà visible, sauf si vous l’avez désactivée. Pour afficher à nouveau la fenêtre, cliquez sur **Déboguer**  >  **fenêtres**  >  **afficher les outils de diagnostic**.

4. Cliquez sur **Déboguer**  >  **Démarrer le débogage** (ou **Démarrer** dans la barre d’outils, ou **F5**).

     Quand l’application est chargée, la vue **Résumé** des outils de diagnostics s’affiche.

5. Pendant que le débogueur est suspendu, activez la collecte des données d’utilisation de l’UC en choisissez **Enregistrer le profil du processeur**, puis ouvrez l’onglet **Utilisation de l’UC**.

     ![Outils de diagnostic - Activer le profilage de l’UC](../profiling/media/quickstart-cpu-usage-summary.png "Outils de diagnostic - Activer le profilage de l’UC")

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

     ![Onglet utilisation de l’UC des outils de diagnostic](../profiling/media/quickstart-cpu-usage-cpu-cplusplus.png "DiagToolsCPUUsageTab")

    > [!TIP]
    > Les fonctions sont classées par ordre et ce sont celles qui effectuent le plus de travail qui figurent en haut de la liste (elles ne sont pas classées selon leur ordre d’appel). Ainsi, vous pouvez identifier rapidement les fonctions avec les temps d’exécution les plus longs.

2. Dans la liste des fonctions, double-cliquez sur la fonction `getNumber`.

    Quand vous double-cliquez sur la fonction, la vue **Appelant/appelé** s’ouvre dans le volet gauche.

    ![Outils de diagnostic - Vue Appelant/appelé](../profiling/media/quickstart-cpu-usage-caller-callee-cplusplus.png "DiagToolsCallerCallee")

    Dans cette vue, la fonction sélectionnée apparaît dans le titre et dans la zone **Fonction active** (ici, `getNumber`). La fonction qui a appelé la fonction active s’affiche sur la gauche sous **Fonctions appelantes**, et toutes les fonctions appelées par la fonction active s’affichent dans la zone **Fonctions appelées** située à droite. Vous pouvez sélectionner l’une ou l’autre de ces zones pour modifier la fonction active.

    Cette vue montre la durée totale (en ms), ainsi que le pourcentage du temps global d’exécution de l’application, nécessaires à l’exécution de la fonction.

    La section **Corps de la fonction** montre également la durée totale (et le pourcentage correspondant) passée dans le corps de la fonction, à l’exclusion du temps passé dans les fonctions appelantes et appelées. (Dans cette illustration, 119 ms sur 43 602 ont été passées dans le corps de la fonction. Le temps restant a été passé dans d’autres parties de code appelées par cette fonction.) Les valeurs réelles seront très différentes, en fonction de votre environnement.

    > [!TIP]
    > Des valeurs élevées dans le **corps de la fonction** peuvent indiquer un goulot d’étranglement de performances au sein de la fonction.

## <a name="next-steps"></a>Étapes suivantes

- [Analyser l’utilisation de la mémoire](../profiling/memory-usage.md) pour identifier les goulots d’étranglement de performances.
- [Analyser l’utilisation de l’UC](../profiling/cpu-usage.md) pour obtenir des informations détaillées sur l’outil d’utilisation de l’UC.
- Analyser l’utilisation de l’UC sans débogueur ou en ciblant une application en cours d’exécution. Pour plus d’informations, consultez la section [Recueillir des données de profilage sans débogage](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) dans [Exécuter des outils de profilage avec ou sans débogueur](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Voir aussi

- [Profilage dans Visual Studio](../profiling/index.yml)
- [Découvrir les outils de profilage](../profiling/profiling-feature-tour.md)
