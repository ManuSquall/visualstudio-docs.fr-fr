---
title: 'Didacticiel : déboguer du code C++'
description: Découvrez les fonctionnalités du débogueur Visual Studio et comment démarrer le débogueur, parcourir le code et inspecter les données dans une application C++.
ms.custom: debug-experiment,  get-started
ms.date: 02/04/2020
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- C++
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8abb517103254aa1e0c89a02b0dc81b38af3ecee
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385251"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>Tutoriel : Apprendre à déboguer C++ avec Visual Studio

Cet article présente les fonctionnalités du débogueur Visual Studio dans une procédure pas à pas. Pour un tour d’horizon plus général des fonctionnalités du débogueur, voir [Présentation du débogueur](../debugger/debugger-feature-tour.md). Quand vous *déboguez votre application*, cela signifie généralement que vous exécutez votre application en y ayant attaché le débogueur. Quand vous faites cela, le débogueur fournit de nombreuses façons de voir ce que fait votre code pendant qu’il s’exécute. Vous pouvez parcourir votre code pas à pas et examiner les valeurs stockées dans les variables, vous pouvez définir des espions sur des variables pour voir quand les valeurs changent, vous pouvez examiner le chemin d’exécution de votre code, voir si une branche de code s’exécute, etc. Si c’est la première fois que vous essayez de déboguer du code, vous pouvez lire [Débogage pour grands débutants](../debugger/debugging-absolute-beginners.md) avant de poursuivre cet article.

Bien que l’application de démonstration soit en C++, la plupart des fonctionnalités s’appliquent à C#, Visual Basic, F #, Python, JavaScript et d’autres langages pris en charge par Visual Studio (F # ne prend pas en charge modifier et continuer. F# et JavaScript ne prennent pas en charge la fenêtre **Automatique**). Les captures d’écran sont en C++.

Ce didacticiel présente les procédures suivantes :

> [!div class="checklist"]
> * Démarrer le débogueur et atteindre des points d’arrêt
> * Découvrir les commandes permettant de parcourir le code pas à pas dans le débogueur
> * Inspecter des variables dans des bulles d’informations et dans les fenêtres du débogueur
> * Examiner la pile des appels

## <a name="prerequisites"></a>Prérequis

::: moniker range=">=vs-2019"

Au préalable, vous devez avoir installé Visual Studio 2019 et la charge de travail **Développement Desktop en C++**.

::: moniker-end
::: moniker range="vs-2017"

Au préalable, vous devez avoir installé Visual Studio 2017 et la charge de travail **Développement Desktop en C++**.

::: moniker-end

::: moniker range="vs-2017"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) pour l’installer gratuitement.

::: moniker-end

::: moniker range=">=vs-2019"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads) pour l’installer gratuitement.

::: moniker-end

::: moniker range="vs-2022"

Si vous n’avez pas encore installé Visual Studio 2022 Preview, accédez à la page [téléchargements Visual studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) pour l’installer gratuitement.

::: moniker-end

Si vous devez installer la charge de travail mais que vous disposez déjà de Visual Studio, accédez à **Outils**  >  **obtenir des outils et des fonctionnalités...**, qui ouvre le Visual Studio installer. Visual Studio Installer est lancé. Choisissez la charge de travail **Développement Desktop en C++**, puis choisissez **Modifier**.

## <a name="create-a-project"></a>Création d’un projet

Tout d’abord, vous allez créer un projet d’application console C++. Le type de projet inclut tous les fichiers de modèle dont vous aurez besoin au départ.

::: moniker range="vs-2017"

1. Ouvrez Visual Studio 2017.

2. Dans la barre de menus supérieure, choisissez **fichier** > **nouveau** > **projet**.

3. Dans la boîte de dialogue **nouveau projet** , dans le volet gauche, développez **Visual C++** , puis choisissez **Bureau Windows**. Dans le volet central, choisissez **application console Windows**. Nommez ensuite le projet *-Démarrer-débogage*.

     Si vous ne voyez pas le modèle de projet d' **application console** , cliquez sur le lien **ouvrir Visual Studio installer** dans le volet gauche de la boîte de dialogue **nouveau projet** . Visual Studio Installer est lancé. Choisissez la charge de travail **Développement multiplateforme .NET Core**, puis choisissez **Modifier**.

4. Cliquez sur **OK**.

   Visual Studio ouvre votre nouveau projet.

::: moniker-end

::: moniker range=">=vs-2019"

1. Ouvrez Visual Studio 2019.

   Si la fenêtre de démarrage n’est pas ouverte  , choisissez > **fenêtre démarrage** de fichier.

1. Dans la fenêtre Démarrer, choisissez **créer un nouveau projet**.

1. Dans la fenêtre **Créer un projet**, entrez ou tapez *console* dans la zone de recherche. Ensuite, choisissez **C++** dans la liste langue, puis choisissez **Windows** dans la liste plateforme. 

   Après avoir appliqué les filtres de langue et de plateforme, choisissez le modèle **application console** , puis cliquez sur **suivant**.

   ![Choisir le modèle C++ pour l’application console](../debugger/media/vs-2019/get-started-create-console-project-cpp.png)

   > [!NOTE]
   > Si vous ne voyez pas le modèle d' **application console** , vous pouvez l’installer à partir de la fenêtre **créer un nouveau projet** . Dans le **Vous ne trouvez pas ce que vous cherchez ?**, choisissez le lien **Installer plus d’outils et de fonctionnalités**. Ensuite, dans la Visual Studio Installer, choisissez la charge de travail **développement Desktop en C++** .

1. Dans la fenêtre **configurer votre nouveau projet** , tapez ou entrez « *Démarrer-démarré-débogage »* dans la zone Nom du **projet** . Ensuite, choisissez **créer**.

   Visual Studio ouvre votre nouveau projet.

::: moniker-end

## <a name="create-the-application"></a>Création de l'application

1. Dans *Get-Started-Debugging. cpp*, remplacez tout le code par défaut par le code suivant à la place :

    ```cpp
    #include <string>
    #include <vector>
    #include <iostream>

    void SendMessage(const std::wstring& name, int msg)
    {
        std::wcout << L"Hello, " << name << L"! Count to " << msg << std::endl;
    }

    int main()
    {
        std::vector<wchar_t> letters = { L'f', L'r', L'e', L'd', L' ', L's', L'm', L'i', L't', L'h' };
        std::wstring name = L"";
        std::vector<int> a(10);
        std::wstring key = L"";

        for (int i = 0; i < letters.size(); i++)
        {
            name += letters[i];
            a[i] = i + 1;
            SendMessage(name, a[i]);
        }
        std::wcin >> key;
        return 0;
    }
    ```

## <a name="start-the-debugger"></a>Démarrez le débogueur !

1. Appuyez sur **F5** (**déboguer > démarrer le débogage**) ou sur le bouton **Démarrer** le débogage ![Démarrer le débogage](../debugger/media/dbg-tour-start-debugging.png "Démarrer le débogage") dans la barre d’outils déboguer.

     **F5** démarre l’application avec le débogueur attaché au processus de l’application, mais jusqu’à présent, nous n’avons rien fait de spécial pour examiner le code. L’application se charge juste et vous voyez la sortie de la console.

    ```cmd
    Hello, f! Count to 1
    Hello, fr! Count to 2
    Hello, fre! Count to 3
    Hello, fred! Count to 4
    Hello, fred ! Count to 5
    Hello, fred s! Count to 6
    Hello, fred sm! Count to 7
    Hello, fred smi! Count to 8
    Hello, fred smit! Count to 9
    Hello, fred smith! Count to 10
    ```

     Dans ce tutoriel, nous examinons cette application plus en détail avec le débogueur et nous regardons les fonctionnalités du débogueur.

2. Arrêtez le débogueur en appuyant sur le bouton rouge arrêter le ![débogage](../debugger/media/dbg-tour-stop-debugging.png "Arrêter le débogage") (**MAJ**  +  **F5**).

3. Dans la fenêtre de console, appuyez sur une touche et **entrée** pour fermer la fenêtre de console.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Définir un point d’arrêt et démarrer le débogueur

1. Dans la boucle `for` de la fonction `main`, définissez un point d’arrêt en cliquant dans la marge gauche de la ligne de code suivante :

    `name += letters[i];`

    Un point d' ![arrêt](../debugger/media/dbg-breakpoint.png "Point d’arrêt") de cercle rouge s’affiche à l’endroit où vous définissez le point d’arrêt.

    Les points d’arrêt sont l’une des fonctionnalités les plus basiques et essentielles du débogage fiable. Quand vous définissez un point d'arrêt, Visual Studio interrompt l'exécution du code à l'emplacement du point d'arrêt pour vous permettre d'examiner les valeurs des variables, le comportement de la mémoire ou encore la bonne exécution ou non d'une branche de code.

2. Appuyez sur **F5** ou cliquez sur le bouton **Démarrer** le débogage ![Démarrer le débogage](../debugger/media/dbg-tour-start-debugging.png "Démarrer le débogage"). l’application démarre et le débogueur s’exécute sur la ligne de code où vous définissez le point d’arrêt.

    ![Définir et atteindre un point d’arrêt](../debugger/media/get-started-set-breakpoint-cpp.png)

    La flèche jaune représente l’instruction sur laquelle le débogueur s’est mis en pause, ce qui interrompt également l’exécution de l’application au même point (cette instruction n’a pas encore été exécutée).

     Si l’application ne s’exécute pas encore, **F5** démarre le débogueur et s’arrête au premier point d’arrêt. Sinon, **F5** continue l’exécution de l’application jusqu’au point d’arrêt suivant.

    Les points d’arrêt sont une fonctionnalité pratique quand vous savez quelle ligne de code ou section de code vous voulez examiner en détail. Pour plus d’informations sur les différents types de points d’arrêt que vous pouvez définir, tels que les points d’arrêt conditionnels, consultez [utilisation de points d’arrêt](../debugger/using-breakpoints.md).

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Parcourir le code dans le débogueur avec les commandes d’exécution pas à pas

Nous utilisons ici principalement des raccourcis clavier, car c’est un bon moyen d’exécuter rapidement votre application dans le débogueur (les commandes équivalentes, comme les commandes des menus, sont indiquées entre parenthèses).

1. Pendant la suspension de la `for` boucle dans la `main` méthode, appuyez sur **F11** (ou sélectionnez **Déboguer > pas à pas** détaillé) à deux reprises pour passer à l’appel de `SendMessage` méthode.

     Après avoir appuyé sur **F11** deux fois, vous devez vous trouver dans la ligne de code suivante :

     `SendMessage(name, a[i]);`

1. Appuyez une fois de plus sur **F11** pour effectuer un pas à pas détaillé dans la `SendMessage` méthode.

     Le pointeur jaune avance dans la `SendMessage` méthode.

     ![Utiliser F11 pour effectuer un pas à pas détaillé dans le code](../debugger/media/get-started-f11-cpp.png "F10 pas à pas détaillé")

     F11 est la commande **Pas à pas détaillé** : elle fait avancer l’exécution de l’application une instruction à la fois. F11 est un bon moyen pour examiner le flux de l’exécution de la façon la plus détaillée. (Pour vous déplacer plus rapidement dans le code, nous vous présenterons également d’autres options.) Par défaut, le débogueur ignore le code non-utilisateur (si vous souhaitez plus d’informations, consultez [uniquement mon code](../debugger/just-my-code.md)).

     Supposons que vous avez terminé d’examiner la `SendMessage` méthode et que vous souhaitez sortir de la méthode tout en restant dans le débogueur. Vous pouvez faire cela avec la commande **Pas à pas sortant**.

1. Appuyez sur **MAJ**  +  **F11** (ou **déboguez > pas à pas sortant**).

     Cette commande reprend l’exécution de l’application (et avance le débogueur) jusqu’à ce que la méthode ou la fonction actuelle retourne.

     Vous devez revenir à la `for` boucle dans la `main` méthode, en pause au niveau de l’appel de la `SendMessage` méthode.

1. Appuyez plusieurs fois sur **F11** jusqu’à ce que vous obteniez à `SendMessage` nouveau l’appel de méthode.

1. Quand vous êtes en pause au niveau de l’appel de méthode, appuyez sur **F10** (ou choisissez **déboguer > pas à pas principal**) une fois.

     ![Utilisez F10 pour effectuer un pas à pas principal dans le code](../debugger/media/get-started-step-over-cpp.png "F10 pas à pas principal")

     Notez que cette fois-ci, le débogueur n’effectue pas de pas à pas détaillé dans la `SendMessage` méthode. **F10** fait avancer le débogueur sans effectuer de pas à pas détaillé dans les fonctions ou les méthodes du code de votre application (le code s’exécute néanmoins). En appuyant sur **F10** sur l’appel de méthode `SendMessage` (au lieu de **F11**), nous avons ignoré le code d’implémentation de `SendMessage` (qui potentiellement ne nous intéresse pas pour l’instant). Pour plus d’informations sur les différentes façons de parcourir votre code, consultez [naviguer dans le code dans le débogueur](../debugger/navigating-through-code-with-the-debugger.md).

## <a name="navigate-code-using-run-to-click"></a>Parcourir le code avec Exécuter jusqu’au clic

1. Appuyez sur **F5** pour passer au point d’arrêt.

1. Dans l’éditeur de code, faites défiler l' `std::wcout` affichage jusqu’à la fonction dans la `SendMessage` méthode jusqu’à ce ![](../debugger/media/dbg-tour-run-to-click.png "RunToClick") que le bouton vert **exécuter pour cliquer** sur s’affiche à gauche. L’info-bulle du bouton indique « Lancer l’exécution jusqu’ici ».

     ![Utiliser la fonctionnalité exécuter pour cliquer](../debugger/media/get-started-run-to-click-cpp.png "Exécuter jusqu’au clic")

   > [!NOTE]
   > Le bouton **Exécuter jusqu’au clic** est une nouveauté de [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]. (Si vous ne voyez pas le bouton fléché vert, utilisez **F11** dans cet exemple plutôt pour faire avancer le débogueur au bon endroit.)

2. Cliquez sur le bouton **exécuter pour cliquer** ![sur.](../debugger/media/dbg-tour-run-to-click.png "RunToClick")

    Le débogueur passe à la `std::wcout` fonction.

    L’utilisation de ce bouton revient à définir un point d’arrêt temporaire. **Exécuter jusqu’au clic** est pratique pour examiner rapidement une zone visible du code d’application (vous pouvez cliquer dans n’importe quel fichier ouvert).

## <a name="restart-your-app-quickly"></a>Redémarrer rapidement votre application

Cliquez sur le bouton **redémarrer** l' ![application de redémarrage](../debugger/media/dbg-tour-restart.png "RestartApp") dans la barre d’outils déboguer (**CTRL**  +  **MAJ**  +  **F5**).

Quand vous appuyez sur **Redémarrer**, vous gagnez du temps par rapport à l’action consistant à arrêter l’application, puis à redémarrer le débogueur. Le débogueur se met en pause sur le premier point d’arrêt qui est atteint par l’exécution du code.

Le débogueur s’arrête à nouveau au point d’arrêt que vous avez défini précédemment à l’intérieur de la `for` boucle.

## <a name="inspect-variables-with-data-tips"></a>Inspecter des variables avec des bulles d’informations (datatips)

Les fonctionnalités qui vous permettent d’inspecter des variables sont parmi les plus pratiques du débogueur : vous pouvez faire cela de différentes façons. Souvent, quand vous essayez de déboguer un problème, vous essayez de déterminer si les variables stockent les valeurs que vous prévoyez à un moment donné.

1. Pendant la suspension de l' `name += letters[i]` instruction, pointez sur la `letters` variable et la valeur par défaut est affichée `size={10}` .

1. Développez la `letters` variable pour afficher ses propriétés, qui incluent tous les éléments contenus dans la variable.

1. Ensuite, pointez sur la `name` variable et vous voyez sa valeur actuelle, une chaîne vide.

1. Appuyez sur **F5** (ou **Déboguer**  >  **Continuer**) plusieurs fois pour effectuer une itération à plusieurs reprises dans la `for` boucle, en interrompant à nouveau au point d’arrêt et en pointant sur la `name` variable chaque fois pour vérifier sa valeur.

     ![Afficher une bulle d’informations](../debugger/media/get-started-data-tip-cpp.png "Afficher une bulle d’informations")

     La valeur de la variable change avec chaque itération de la `for` boucle, en présentant les valeurs de `f` , puis, puis `fr` `fre` , et ainsi de suite.

     Souvent, lors du débogage, vous voulez un moyen rapide de vérifier les valeurs des propriétés sur des variables pour voir si elles stockent bien les valeurs prévues. Les bulles d’informations (« data tips ») sont un bon moyen de le faire.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Inspecter des variables avec les Fenêtres Automatique et Variables locales

1. Examinez la fenêtre **Automatique** en bas de l’éditeur de code.

    S’il est fermé, ouvrez-le en étant suspendu dans le débogueur en sélectionnant **Déboguer**  >  **Windows**  >  **automatique**.

    Dans la fenêtre **Automatique**, vous voyez des variables et leur valeur actuelle. La fenêtre **Automatique** montre toutes les variables utilisées dans la ligne active ou la ligne précédente (consultez la documentation pour les comportements selon le langage).

1. Ensuite, examinons la fenêtre **Variables locales**, sous un onglet à côté de la fenêtre **Automatique**.

1. Développez la `letters` variable pour afficher les éléments qu’elle contient.

     ![Inspecter les variables dans la fenêtre variables locales](../debugger/media/get-started-locals-window-cpp.png "Variables locales (fenêtre)")

    La fenêtre **Variables locales** montre les variables qui se trouvent dans l’[étendue](https://www.wikipedia.org/wiki/Scope_(computer_science)) actuelle, c’est-à-dire le contexte d’exécution actif.

## <a name="set-a-watch"></a>Définir un espion

1. Dans la fenêtre principale de l’éditeur de code, cliquez avec le bouton droit sur la `name` variable et choisissez **Ajouter un espion**.

    La fenêtre **Espion** s’ouvre en bas de l’éditeur de code. Vous pouvez utiliser une fenêtre **Espion** pour spécifier une variable (ou une expression) que vous voulez observer.

    À présent, vous avez un espion défini sur la `name` variable et vous pouvez voir sa valeur changer à mesure que vous parcourez le débogueur. Contrairement à d’autres fenêtres de variables, la fenêtre **Espion** montre toujours les variables que vous observez (elles apparaissent en grisé quand elles sont en dehors de l’étendue).

## <a name="examine-the-call-stack"></a>Examiner la pile des appels

1. Alors que l’exécution est mise en pause dans la boucle `for`, cliquez sur la fenêtre **Pile des appels** qui est ouverte par défaut dans le volet inférieur droit.

    S’il est fermé, ouvrez-le en étant suspendu dans le débogueur en sélectionnant **Déboguer** la pile des  >    >  **appels** Windows.

2. Cliquez sur **F11** plusieurs fois jusqu’à ce que le débogueur soit suspendu dans la `SendMessage` méthode. Regardez la fenêtre **Pile des appels**.

    ![Examiner la pile des appels](../debugger/media/get-started-call-stack-cpp.png "ExamineCallStack")

    La fenêtre **Pile des appels** montre l’ordre dans lequel les méthodes et les fonctions sont appelées. La ligne du haut montre la fonction active (méthode `SendMessage` dans cette application). La deuxième ligne montre que `SendMessage` a été appelée à partir de la méthode `main`, etc.

   > [!NOTE]
   > La fenêtre **Pile des appels** est similaire à la perspective Débogage dans certains IDE, comme Eclipse.

    La pile des appels est un bon moyen d’examiner et de comprendre le flux d’exécution d’une application.

    Vous pouvez double-cliquer sur une ligne de code pour accéder à ce code source ; ceci change également l’étendue active inspectée par le débogueur. Cette action ne fait pas avancer le débogueur.

    Vous pouvez également utiliser les menus contextuels de la fenêtre **Pile des appels** pour faire d’autres choses. Par exemple, vous pouvez insérer des points d’arrêt dans des fonctions spécifiées, faire avancer le débogueur avec **Exécuter jusqu’au curseur** et aller examiner le code source. Pour plus d’informations, consultez [Guide pratique pour examiner la pile des appels](../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Changer le flux d’exécution

1. Appuyez deux fois sur **F11** pour exécuter la `std::wcout` fonction.

1. Après avoir suspendu le débogueur dans l' `SendMessage` appel de méthode, utilisez la souris pour saisir la flèche jaune (le pointeur d’exécution) à gauche et déplacer la flèche jaune d’une ligne vers le haut `std::wcout` .

1. Appuyez sur **F11**.

    Le débogueur réexécute la `std::wcout` fonction (vous voyez cela dans la sortie de la fenêtre de console).

    En changeant le flux d’exécution, vous pouvez effectuer des opérations comme tester d’autres chemins d’exécution du code ou réexécuter du code sans devoir redémarrer le débogueur.

    > [!WARNING]
    > Vous devez rester prudent avec cette fonctionnalité, vous pouvez voir un avertissement dans l’info-bulle. Vous pouvez aussi en voir d’autres. Le fait de déplacer le pointeur ne peut pas rétablir votre application à un état antérieur.

1. Appuyez sur **F5** pour poursuivre l’exécution de l’application.

    Félicitations ! Vous avez terminé ce didacticiel.

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez découvert comment démarrer le débogueur, parcourir le code pas à pas et inspecter des variables. Vous pouvez obtenir une présentation générale des fonctionnalités du débogueur et suivre des liens qui donnent accès à plus d’informations.

> [!div class="nextstepaction"]
> [Présentation du débogueur](../debugger/debugger-feature-tour.md)

