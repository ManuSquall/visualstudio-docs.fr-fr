---
title: 'Didacticiel : déboguer le code Visual Basic'
description: Découvrez comment démarrer le débogueur Visual Studio, parcourir le code et inspecter les données.
ms.custom: debug-experiment, seodec18, get-started
ms.date: 11/27/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- CSharp
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9b38089a088186a30ebd13cae68d19ac23235bf9
ms.sourcegitcommit: 697f2ab875fd789685811687387e9e8e471a38c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74829986"
---
# <a name="tutorial-learn-to-debug-visual-basic-code-using-visual-studio"></a>Tutoriel : Apprendre à déboguer du code Visual Basic avec Visual Studio

Cet article présente les fonctionnalités du débogueur Visual Studio dans une procédure pas à pas. Pour un tour d’horizon plus général des fonctionnalités du débogueur, voir [Présentation du débogueur](../../debugger/debugger-feature-tour.md). Quand vous *déboguez votre application*, cela signifie généralement que vous exécutez votre application en y ayant attaché le débogueur. Quand vous faites cela, le débogueur fournit de nombreuses façons de voir ce que fait votre code pendant qu’il s’exécute. Vous pouvez parcourir votre code pas à pas et examiner les valeurs stockées dans les variables, vous pouvez définir des espions sur des variables pour voir quand les valeurs changent, vous pouvez examiner le chemin d’exécution de votre code, voir si une branche de code s’exécute, etc. Si c’est la première fois que vous essayez de déboguer du code, vous pouvez lire [Débogage pour grands débutants](../../debugger/debugging-absolute-beginners.md) avant de poursuivre cet article.

Dans ce didacticiel, vous allez effectuer les actions suivantes :

> [!div class="checklist"]
> * Démarrer le débogueur et atteindre des points d’arrêt
> * Découvrir les commandes permettant de parcourir le code pas à pas dans le débogueur
> * Inspecter des variables dans des bulles d’informations et dans les fenêtres du débogueur
> * Examiner la pile des appels

## <a name="prerequisites"></a>Configuration requise

::: moniker range=">=vs-2019"

Visual Studio 2019 et la charge de travail **Développement .NET Desktop** doivent être installés.

::: moniker-end
::: moniker range="vs-2017"

Au préalable, vous devez avoir installé Visual Studio 2017 et la charge de travail **Développement .NET Desktop**.

::: moniker-end

::: moniker range="vs-2017"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) pour l’installer gratuitement.

::: moniker-end

::: moniker range="vs-2019"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads) pour l’installer gratuitement.

::: moniker-end

Si vous devez installer la charge de travail, mais que vous avez déjà installé Visual Studio, cliquez sur **Outils** > **Obtenir les outils et fonctionnalités...** , qui ouvre Visual Studio Installer. Visual Studio Installer est lancé. Choisissez la charge de travail **Développement .NET Desktop**, puis choisissez **Modifier**.

## <a name="create-a-project"></a>Créer un projet

1. Ouvrez Visual Studio.

    ::: moniker range=">=vs-2019"
    Appuyez sur **Échap** pour fermer la fenêtre de démarrage. Tapez **CTRL + Q** pour ouvrir la zone de recherche, tapez **Visual Basic**, choisissez **modèles**, puis choisissez **créer un projet d’application console (.net Core)** ou **créer un projet d’application console (.NET Framework)** . Dans la boîte de dialogue qui s’affiche, tapez un nom comme **get-started-debugging**, puis choisissez **Créer**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet**. Dans le volet gauche de la boîte de dialogue **Nouveau projet**, sous **Visual Basic**, choisissez **Windows Desktop** puis, dans le volet central, choisissez **Application console (.NET Framework)** . Ensuite, tapez un nom comme **get-started-debugging**, puis cliquez sur **OK**.
    ::: moniker-end

    Si vous ne voyez pas le modèle de projet **Application console (.NET Framework)** , accédez à **Outils** > **Obtenir les outils et fonctionnalités...** , qui ouvre Visual Studio Installer. Choisissez la charge de travail **Développement .NET Desktop**, puis choisissez **Modifier**.

    Visual Studio crée le projet.

1. Dans *Module1. vb*, remplacez tout le code par défaut

    ```vb
    Module Module1

        Sub Main()
        End Sub

    End Module
    ```

    par le code suivant :

    ```vb
    Imports System
    Imports System.Collections.Generic

    Public Class Shape

      ' A few example members
        Public Property X As Integer
            Get
                Return X
            End Get
            Set
            End Set
        End Property

        Public Property Y As Integer
            Get
                Return Y
            End Get
            Set
            End Set
        End Property

        Public Property Height As Integer
            Get
                Return Height
            End Get
            Set
            End Set
        End Property

        Public Property Width As Integer
            Get
                Return Width
            End Get
            Set
            End Set
        End Property

        ' Virtual method
        Public Overridable Sub Draw()
            Console.WriteLine("Performing base class drawing tasks")
        End Sub
    End Class

    Public Class Circle
        Inherits Shape

        Public Overrides Sub Draw()
            ' Code to draw a circle...
            Console.WriteLine("Drawing a circle")
            MyBase.Draw()
        End Sub
    End Class

    Public Class Rectangle
        Inherits Shape

        Public Overrides Sub Draw()
            ' Code to draw a rectangle...
            Console.WriteLine("Drawing a rectangle")
            MyBase.Draw()
        End Sub
    End Class

    Public Class Triangle
        Inherits Shape

        Public Overrides Sub Draw()
            ' Code to draw a triangle...
            Console.WriteLine("Drawing a trangle")
            MyBase.Draw()
        End Sub
    End Class

    Module Module1

        Sub Main(ByVal args() As String)

            Dim shapes = New List(Of Shape) From
            {
                New Rectangle,
                New Triangle,
                New Circle
            }

            For Each shape In shapes
                shape.Draw()
            Next
            ' Keep the console open in debug mode.
            Console.WriteLine("Press any key to exit.")
            Console.ReadKey()

        End Sub

    End Module

    ' Output:
    '    Drawing a rectangle
    '    Performing base class drawing tasks
    '    Drawing a triangle
    '    Performing base class drawing tasks
    '    Drawing a circle
    '    Performing base class drawing tasks
    ```

## <a name="start-the-debugger"></a>Démarrez le débogueur !

1. Appuyez sur **F5** (**déboguer > Démarrer le débogage**) ou sur le bouton **Démarrer** le débogage ![Démarrer le débogage](../../debugger/media/dbg-tour-start-debugging.png "Lancement du débogage") dans la barre d’outils déboguer.

     **F5** démarre l’application avec le débogueur attaché au processus de l’application, mais jusqu’à présent, nous n’avons rien fait de spécial pour examiner le code. L’application se charge juste et vous voyez la sortie de la console.

    ```cmd
    Drawing a rectangle
    Performing base class drawing tasks
    Drawing a triangle
    Performing base class drawing tasks
    Drawing a circle
    Performing base class drawing tasks
    ```

     Dans ce tutoriel, nous examinons cette application plus en détail avec le débogueur et nous regardons les fonctionnalités du débogueur.

2. Arrêtez le débogueur en appuyant sur le bouton rouge arrêter ![arrêter le débogage](../../debugger/media/dbg-tour-stop-debugging.png "Arrêter le débogage") .

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Définir un point d’arrêt et démarrer le débogueur

1. Dans la boucle `For Each` de la fonction `Main`, définissez un point d’arrêt en cliquant dans la marge gauche de la ligne de code suivante :

    `shape.Draw()`

    Un cercle rouge apparaît là où vous avez défini le point d’arrêt.

    ![Définir un point d'arrêt](../visual-basic/media/get-started-set-breakpoint-vb.png)

    Les points d'arrêt constituent une fonctionnalité élémentaire et essentielle de toute procédure de débogage fiable. Quand vous définissez un point d'arrêt, Visual Studio interrompt l'exécution du code à l'emplacement du point d'arrêt pour vous permettre d'examiner les valeurs des variables, le comportement de la mémoire ou encore la bonne exécution ou non d'une branche de code.

2. Appuyez sur **F5** ou cliquez sur le bouton **Démarrer** le débogage ![Démarrer le débogage](../../debugger/media/dbg-tour-start-debugging.png "Lancement du débogage"). l’application démarre et le débogueur s’exécute sur la ligne de code où vous définissez le point d’arrêt.

    ![Atteindre un point d’arrêt](../visual-basic/media/get-started-hit-breakpoint-vb.png)

    La flèche jaune représente l’instruction sur laquelle le débogueur s’est mis en pause, ce qui interrompt également l’exécution de l’application au même point (cette instruction n’a pas encore été exécutée).

     Si l’application ne s’exécute pas encore, **F5** démarre le débogueur et s’arrête au premier point d’arrêt. Sinon, **F5** continue l’exécution de l’application jusqu’au point d’arrêt suivant.

    Les points d’arrêt sont une fonctionnalité pratique quand vous savez quelle ligne de code ou section de code vous voulez examiner en détail.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Parcourir le code dans le débogueur avec les commandes d’exécution pas à pas

Nous utilisons ici principalement des raccourcis clavier, car c’est un bon moyen d’exécuter rapidement votre application dans le débogueur (les commandes équivalentes, comme les commandes des menus, sont indiquées entre parenthèses).

1. Alors que l’exécution est mise en pause dans l’appel de la méthode `shape.Draw` dans la fonction `Main`, appuyez sur **F11** (ou choisissez **Déboguer > Pas à pas détaillé**) pour avancer dans le code de la classe `Rectangle`.

     ![Utiliser F11 pour effectuer un pas à pas détaillé dans le code](../visual-basic/media/get-started-f11-vb.png "F11 pas à pas détaillé")

     F11 est la commande **Pas à pas détaillé** : elle fait avancer l’exécution de l’application une instruction à la fois. F11 est un bon moyen pour examiner le flux de l’exécution de la façon la plus détaillée. (Pour vous déplacer plus rapidement dans le code, nous vous présenterons également d’autres options.) Par défaut, le débogueur ignore le code non-utilisateur (si vous souhaitez plus d’informations, consultez [uniquement mon code](../../debugger/just-my-code.md)).

2. Appuyez plusieurs fois sur **F10** (ou choisissez **Déboguer > Pas à pas principal**) jusqu’à ce que le débogueur s’arrête à l’appel de la méthode `MyBase.Draw`, puis appuyez sur **F10** encore une fois.

     ![Utilisez F10 pour effectuer un pas à pas principal dans le code](../visual-basic/media/get-started-step-over-vb.png "F10 pas à pas principal")

     Notez que cette fois, le débogueur n’effectue pas de pas à pas détaillé dans la méthode `Draw` de la classe de base (`Shape`). **F10** fait avancer le débogueur sans effectuer de pas à pas détaillé dans les fonctions ou les méthodes du code de votre application (le code s’exécute néanmoins). En appuyant sur **F10** sur l’appel de méthode `MyBase.Draw` (au lieu de **F11**), nous avons ignoré le code d’implémentation de `MyBase.Draw` (qui potentiellement ne nous intéresse pas pour l’instant).

## <a name="navigate-code-using-run-to-click"></a>Parcourir le code avec Exécuter jusqu’au clic

1. Dans l’éditeur de code, faites défiler ![l’affichage jusqu'](../../debugger/media/dbg-tour-run-to-click.png "RunToClick") à la méthode `Console.WriteLine` dans la classe `Triangle` jusqu’à ce que le bouton vert **exécuter pour cliquer** sur s’affiche à gauche. L’info-bulle du bouton indique « Lancer l’exécution jusqu’ici ».

     ![Utiliser la fonctionnalité exécuter pour cliquer](../visual-basic/media/get-started-run-to-click-vb.png "Exécuter jusqu’au clic")

   > [!NOTE]
   > Le bouton **Exécuter jusqu’au clic** est une nouveauté de [!include[vs_dev15](../../misc/includes/vs_dev15_md.md)]. Si vous ne voyez pas le bouton avec la flèche verte, utilisez à la place **F11** dans cet exemple pour faire avancer le débogueur jusqu’au bon endroit.

2. Cliquez sur le bouton **exécuter pour cliquer** ![sur.](../../debugger/media/dbg-tour-run-to-click.png "RunToClick")

    L’utilisation de ce bouton revient à définir un point d’arrêt temporaire. **Exécuter jusqu’au clic** est pratique pour examiner rapidement une zone visible du code d’application (vous pouvez cliquer dans n’importe quel fichier ouvert).

    Le débogueur avance jusqu’à l’implémentation de la méthode `Console.WriteLine` pour la classe `Triangle`. (Si le débogueur suspend d’abord au point d’arrêt que vous avez défini précédemment, utilisez **exécuter pour cliquer** à nouveau pour faire avancer le débogueur pour `Console.WriteLine`.)

    Alors que l’application est mise en pause, vous remarquez une faute de frappe ! La sortie « Drawing a trangle » est mal orthographiée. Nous pouvons la corriger directement ici pendant l’exécution de l’application dans le débogueur.

## <a name="edit-code-and-continue-debugging"></a>Modifier le code et continuer le débogage

1. Cliquez dans « Drawing a trangle » et corrigez en remplaçant « trangle » par « triangle ».

1. Appuyez une fois sur **F11** : vous voyez que le débogueur avance à nouveau.

    > [!NOTE]
    > Selon le type de code que vous modifiez dans le débogueur, vous pouvez voir un message d’avertissement. Dans certains scénarios, vous devez recompiler le code avant de pouvoir continuer.

## <a name="step-out"></a>Pas à pas sortant

Supposons que vous avez terminé d’examiner la méthode `Draw` de la classe `Triangle` et que vous voulez quitter la fonction, mais rester dans le débogueur. Vous pouvez faire cela avec la commande **Pas à pas sortant**.

1. Appuyez sur **Maj** + **F11** (ou **Déboguer > Pas à pas sortant**).

     Cette commande reprend l’exécution de l’application (et fait avancer le débogueur) jusqu’au retour de la fonction active.

     Vous devez normalement être revenu dans la boucle `For Each` de la méthode `Main`. Si ce n’est pas le cas, appuyez sur **maj** + **F11** une deuxième fois.

## <a name="restart-your-app-quickly"></a>Redémarrer rapidement votre application

Cliquez sur le bouton **redémarrer l'** ![application de redémarrage](../../debugger/media/dbg-tour-restart.png "RestartApp") dans la barre d’outils déboguer (**CTRL** + **MAJ** + **F5**).

Quand vous appuyez sur **Redémarrer**, vous gagnez du temps par rapport à l’action consistant à arrêter l’application, puis à redémarrer le débogueur. Le débogueur se met en pause sur le premier point d’arrêt qui est atteint par l’exécution du code.

Le débogueur s’arrête à nouveau au niveau du point d’arrêt que vous définissez, à la méthode `shape.Draw()`.

## <a name="inspect-variables-with-data-tips"></a>Inspecter des variables avec des bulles d’informations (datatips)

Les fonctionnalités qui vous permettent d’inspecter des variables sont parmi les plus pratiques du débogueur : vous pouvez faire cela de différentes façons. Souvent, quand vous essayez de déboguer un problème, vous essayez de déterminer si les variables stockent les valeurs que vous prévoyez à un moment donné.

1. Alors que l’exécution est mise en pause dans la méthode `shape.Draw()`, placez le curseur sur l’objet `shapes`. Vous voyez alors sa valeur de propriété par défaut, la propriété `Count`.

1. Développez l’objet `shapes` pour voir toutes ses propriétés, comme le premier index du tableau `[0]`, qui a la valeur `Rectangle`.

     ![Afficher une bulle d’informations](../visual-basic/media/get-started-data-tip-vb.png "Afficher une bulle d’informations")

    Vous pouvez développer davantage les objets pour voir leurs propriétés, comme la propriété `Height` du rectangle.

    Souvent, lors du débogage, vous voulez un moyen rapide de vérifier les valeurs des propriétés sur des objets : les datatips sont un bon moyen de le faire.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Inspecter des variables avec les Fenêtres Automatique et Variables locales

1. Examinez la fenêtre **Automatique** en bas de l’éditeur de code.

     ![Inspecter les variables dans la fenêtre automatique](../visual-basic/media/get-started-autos-window-vb.png "Fenêtre automatique")

    Dans la fenêtre **Automatique**, vous voyez des variables et leur valeur actuelle. La fenêtre **Automatique** montre toutes les variables utilisées dans la ligne active ou la ligne précédente (consultez la documentation pour les comportements selon le langage).

2. Ensuite, examinons la fenêtre **Variables locales**, sous un onglet à côté de la fenêtre **Automatique**.

    La fenêtre **Variables locales** montre les variables qui se trouvent dans l’[étendue](https://www.wikipedia.org/wiki/Scope_(computer_science)) actuelle, c’est-à-dire le contexte d’exécution actif.

## <a name="set-a-watch"></a>Définir un espion

1. Dans la fenêtre principale de l’éditeur de code, cliquez sur l’objet `shapes` et choisissez **Ajouter un espion**.

    La fenêtre **Espion** s’ouvre en bas de l’éditeur de code. Vous pouvez utiliser une fenêtre **Espion** pour spécifier une variable (ou une expression) que vous voulez observer.

    Vous avez maintenant un espion défini sur l’objet `shapes` et vous pouvez voir sa valeur changer au fil de votre déplacement dans le débogueur. Contrairement à d’autres fenêtres de variables, la fenêtre **Espion** montre toujours les variables que vous observez (elles apparaissent en grisé quand elles sont en dehors de l’étendue).

## <a name="examine-the-call-stack"></a>Examiner la pile des appels

1. Alors que l’exécution est mise en pause dans la boucle `For Each`, cliquez sur la fenêtre **Pile des appels** qui est ouverte par défaut dans le volet inférieur droit.

2. Appuyez plusieurs fois sur **F11** jusqu’à ce que le débogueur fasse une pause dans la méthode `MyBase.Draw` de la classe `Rectangle` dans l’éditeur de code. Regardez la fenêtre **Pile des appels**.

    ![Examiner la pile des appels](../visual-basic/media/get-started-call-stack-vb.png "ExamineCallStack")

    La fenêtre **Pile des appels** montre l’ordre dans lequel les méthodes et les fonctions sont appelées. La ligne du haut montre la fonction active (méthode `Rectangle.Draw` dans cette application). La deuxième ligne montre que `Rectangle.Draw` a été appelée à partir de la fonction `Main`, etc.

   > [!NOTE]
   > La fenêtre **Pile des appels** est similaire à la perspective Débogage dans certains IDE, comme Eclipse.

    La pile des appels est un bon moyen d’examiner et de comprendre le flux d’exécution d’une application.

    Vous pouvez double-cliquer sur une ligne de code pour accéder à ce code source ; ceci change également l’étendue active inspectée par le débogueur. Cette action ne fait pas avancer le débogueur.

    Vous pouvez également utiliser les menus contextuels de la fenêtre **Pile des appels** pour faire d’autres choses. Par exemple, vous pouvez insérer des points d’arrêt dans des fonctions spécifiées, faire avancer le débogueur avec **Exécuter jusqu’au curseur** et aller examiner le code source. Pour plus d’informations, consultez [Guide pratique pour examiner la pile des appels](../../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Changer le flux d’exécution

1. Alors que le débogueur est mis en pause dans l’appel de la méthode `MyBase.Draw`, de la classe `Rectangle`, utilisez la souris pour sélectionner la flèche jaune (pointeur d’exécution) sur la gauche, puis déplacez la flèche jaune d’une ligne vers le haut, où est fait l’appel de la méthode `Console.WriteLine`.

1. Appuyez sur **F11**.

    Le débogueur réexécute la méthode `Console.WriteLine` (vous voyez une sortie en double dans la sortie de la fenêtre de console).

    En changeant le flux d’exécution, vous pouvez effectuer des opérations comme tester d’autres chemins d’exécution du code ou réexécuter du code sans devoir redémarrer le débogueur.

    > [!WARNING]
    > Vous devez rester prudent avec cette fonctionnalité, vous pouvez voir un avertissement dans l’info-bulle. Vous pouvez aussi en voir d’autres. Le fait de déplacer le pointeur ne peut pas rétablir votre application à un état antérieur.

1. Appuyez sur **F5** pour poursuivre l’exécution de l’application.

    Félicitations ! Vous avez terminé ce didacticiel.

## <a name="next-steps"></a>Étapes suivantes :

Dans ce tutoriel, vous avez découvert comment démarrer le débogueur, parcourir le code pas à pas et inspecter des variables. Vous pouvez obtenir une présentation générale des fonctionnalités du débogueur et suivre des liens qui donnent accès à plus d’informations.

> [!div class="nextstepaction"]
> [Présentation du débogueur](../../debugger/debugger-feature-tour.md)
