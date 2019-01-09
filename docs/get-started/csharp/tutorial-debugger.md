---
title: 'Tutoriel : Déboguer le code C#'
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1590bbbe53a164ff9e59b887f7161b45a7d62361
ms.sourcegitcommit: a715de2ba8c703f37aa2102567b1aa2c0f05a117
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2018
ms.locfileid: "53441932"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>Tutoriel : Apprendre à déboguer le code C# avec Visual Studio

Cet article présente les fonctionnalités du débogueur Visual Studio dans une procédure pas à pas. Si vous voulez une vue plus générale des fonctionnalités du débogueur, consultez [Présentation du débogueur](../../debugger/debugger-feature-tour.md). Quand vous *déboguez votre application*, cela signifie généralement que vous exécutez votre application en y ayant attaché le débogueur. Quand vous faites cela, le débogueur fournit de nombreuses façons de voir ce que fait votre code pendant qu’il s’exécute. Vous pouvez parcourir votre code pas à pas et examiner les valeurs stockées dans les variables, vous pouvez définir des espions sur des variables pour voir quand les valeurs changent, vous pouvez examiner le chemin d’exécution de votre code, voir si une branche de code s’exécute, etc. Si c’est la première fois que vous essayez de déboguer du code, vous pouvez lire [Débogage pour grands débutants](../../debugger/debugging-absolute-beginners.md) avant de poursuivre cet article.

| | |
|---------|---------|
| ![Icône représentant une caméra pour les vidéos](../../install/media/video-icon.png "Regarder une vidéo") | [Regardez une vidéo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugger-Feature-tour-of-Visual-studio-2017-sqwiwLD6D_1111787171) sur le débogage, qui montre des étapes similaires. |

Bien que l’application de démonstration soit écrite en C#, la plupart des fonctionnalités sont applicables à C++, Visual Basic, F#, Python, JavaScript et d’autres langages pris en charge par Visual Studio (F# ne prend pas en charge Modifier et continuer. F# et JavaScript ne prennent pas en charge la fenêtre **Automatique**). Les captures d’écran sont en C#.

Dans ce didacticiel, vous allez effectuer les actions suivantes :

> [!div class="checklist"]
> * Démarrer le débogueur et atteindre des points d’arrêt
> * Découvrir les commandes permettant de parcourir le code pas à pas dans le débogueur
> * Inspecter des variables dans des bulles d’informations et dans les fenêtres du débogueur
> * Examiner la pile des appels

## <a name="prerequisites"></a>Prérequis

* Au préalable, vous devez avoir installé Visual Studio 2017 et la charge de travail **Développement .NET Desktop**.

    Si vous n’avez pas encore installé Visual Studio, accédez à la page  [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)  pour l’installer gratuitement.

    Si vous devez installer la charge de travail mais que vous avez déjà Visual Studio, cliquez sur le lien **Ouvrir Visual Studio Installer** dans le volet gauche de la boîte de dialogue **Nouveau projet** (sélectionnez **Fichier** > **Nouveau** > **Projet**). Visual Studio Installer est lancé. Choisissez la charge de travail **Développement .NET Desktop**, puis choisissez **Modifier**.

## <a name="create-a-project"></a>Créer un projet

1. Dans Visual Studio, sélectionnez **Fichier > Nouveau projet**.

2. Sous **Visual C#**, choisissez **Windows Desktop** puis, dans le volet central, **Application console**.

    Si vous ne voyez pas le modèle de projet **Application console**, cliquez sur le lien **Ouvrir Visual Studio Installer** dans le volet gauche de la boîte de dialogue **Nouveau projet**. Visual Studio Installer est lancé. Choisissez la charge de travail *Développement .NET Desktop**, puis **Modifier**.

3. Tapez un nom comme **get-started-debugging**, puis cliquez sur **OK**.

    Visual Studio crée le projet.

4. Dans *Program.cs*, remplacez le code suivant

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;

    namespace get_started_debugging
    {
        class Program
        {
            static void Main(string[] args)
            {
            }
        }
    }
    ```

    par le code suivant :

    ```csharp
    using System;
    using System.Collections.Generic;

    public class Shape
    {
        // A few example members
        public int X { get; private set; }
        public int Y { get; private set; }
        public int Height { get; set; }
        public int Width { get; set; }
   
        // Virtual method
        public virtual void Draw()
        {
            Console.WriteLine("Performing base class drawing tasks");
        }
    }

    class Circle : Shape
    {
        public override void Draw()
        {
            // Code to draw a circle...
            Console.WriteLine("Drawing a circle");
            base.Draw();
        }
    }

    class Rectangle : Shape
    {
        public override void Draw()
        {
            // Code to draw a rectangle...
            Console.WriteLine("Drawing a rectangle");
            base.Draw();
        }
    }

    class Triangle : Shape
    {
        public override void Draw()
        {
            // Code to draw a triangle...
            Console.WriteLine("Drawing a trangle");
            base.Draw();
        }
    }

    class Program
    {
        static void Main(string[] args)
        {

            var shapes = new List<Shape>
            {
                new Rectangle(),
                new Triangle(),
                new Circle()
            };

            foreach (var shape in shapes)
            {
                shape.Draw();
            }

            // Keep the console open in debug mode.
            Console.WriteLine("Press any key to exit.");
            Console.ReadKey();
        }

    }

    /* Output:
        Drawing a rectangle
        Performing base class drawing tasks
        Drawing a triangle
        Performing base class drawing tasks
        Drawing a circle
        Performing base class drawing tasks
    */
    ```

## <a name="start-the-debugger"></a>Démarrez le débogueur !

1. Appuyez sur **F5** (**Déboguer > Démarrer le débogage**) ou sur le bouton **Démarrer le débogage** ![Démarrer le débogage](../../debugger/media/dbg-tour-start-debugging.png "Démarrer le débogage ") dans la barre d’outils Débogage.

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

2. Arrêtez le débogueur en appuyant sur le bouton d’arrêt rouge ![Arrêter le débogage](../../debugger/media/dbg-tour-stop-debugging.png "Arrêter le débogage").

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Définir un point d’arrêt et démarrer le débogueur

1. Dans la boucle `foreach` de la fonction `Main`, définissez un point d’arrêt en cliquant dans la marge gauche de la ligne de code suivante :

    `shape.Draw()`

    Un cercle rouge apparaît là où vous avez défini le point d’arrêt.

    Les points d'arrêt constituent une fonctionnalité élémentaire et essentielle de toute procédure de débogage fiable. Quand vous définissez un point d'arrêt, Visual Studio interrompt l'exécution du code à l'emplacement du point d'arrêt pour vous permettre d'examiner les valeurs des variables, le comportement de la mémoire ou encore la bonne exécution ou non d'une branche de code. 

2. Appuyez sur **F5** ou cliquez sur le bouton **Démarrer le débogage** ![Démarrer le débogage](../../debugger/media/dbg-tour-start-debugging.png "Démarrer le débogage"), l’application démarre et le débogueur s’exécute jusqu’à la ligne de code où vous avez défini le point d’arrêt.

    ![Définir et atteindre un point d’arrêt](../csharp/media/get-started-set-breakpoint.gif)

    La flèche jaune représente l’instruction sur laquelle le débogueur s’est mis en pause, ce qui interrompt également l’exécution de l’application au même point (cette instruction n’a pas encore été exécutée).

     Si l’application ne s’exécute pas encore, **F5** démarre le débogueur et s’arrête au premier point d’arrêt. Sinon, **F5** continue l’exécution de l’application jusqu’au point d’arrêt suivant.

    Les points d’arrêt sont une fonctionnalité pratique quand vous savez quelle ligne de code ou section de code vous voulez examiner en détail.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Parcourir le code dans le débogueur avec les commandes d’exécution pas à pas

Nous utilisons ici principalement des raccourcis clavier, car c’est un bon moyen d’exécuter rapidement votre application dans le débogueur (les commandes équivalentes, comme les commandes des menus, sont indiquées entre parenthèses).

1. Alors que l’exécution est mise en pause dans l’appel de la méthode `shape.Draw` dans la méthode `Main`, appuyez sur **F11** (ou choisissez **Déboguer > Pas à pas détaillé**) pour avancer dans le code de la classe `Rectangle`.

     ![Utilisez F11 pour exécuter le code en pas à pas détaillé](../csharp/media/get-started-f11.png "F11 Pas à pas détaillé")

     F11 est la commande **Pas à pas détaillé** : elle fait avancer l’exécution de l’application une instruction à la fois. F11 est un bon moyen pour examiner le flux de l’exécution de la façon la plus détaillée. (Pour avancer plus rapidement dans le code, il existe d’autres options, que nous allons vous montrer.) Par défaut, le débogueur ignore le code non-utilisateur (si vous voulez plus d’informations, consultez [Uniquement mon code](../../debugger/just-my-code.md)).

2. Appuyez plusieurs fois sur **F10** (ou choisissez **Déboguer > Pas à pas principal**) jusqu’à ce que le débogueur s’arrête à l’appel de la méthode `base.Draw`, puis appuyez sur **F10** encore une fois.

     ![Utiliser la touche F10 pour effectuer un pas à pas principal dans le code](../csharp/media/get-started-step-over.png "F10 Pas à pas principal")

     Notez que cette fois, le débogueur n’effectue pas de pas à pas détaillé dans la méthode `Draw` de la classe de base (`Shape`). **F10** fait avancer le débogueur sans effectuer de pas à pas détaillé dans les fonctions ou les méthodes du code de votre application (le code s’exécute néanmoins). En appuyant sur **F10** sur l’appel de la méthode `base.Draw` (au lieu de **F11**), nous avons ignoré le code d’implémentation pour `base.Draw` (qui ne nous intéresse peut-être pas pour l’instant).

## <a name="navigate-code-using-run-to-click"></a>Parcourir le code avec Exécuter jusqu’au clic

1. Dans l’éditeur de code, faites défiler vers le bas et placez le curseur sur la méthode `Console.WriteLine` dans la classe `Triangle` jusqu’à ce que le bouton vert **Exécuter jusqu’au clic** ![Exécuter jusqu’au clic](../../debugger/media/dbg-tour-run-to-click.png "RunToClick") apparaisse à gauche. L’info-bulle pour le bouton affiche « Exécuter l’exécution jusqu’ici ».

     ![Utiliser la fonctionnalité Exécuter jusqu’au clic](../csharp/media/get-started-run-to-click.png "Exécuter jusqu’au clic")

   > [!NOTE]
   > Le bouton **Exécuter jusqu’au clic** est une nouveauté de [!include[vs_dev15](../../misc/includes/vs_dev15_md.md)]. Si vous ne voyez pas le bouton avec la flèche verte, utilisez à la place **F11** dans cet exemple pour faire avancer le débogueur jusqu’au bon endroit.

2. Cliquez sur le bouton **Exécuter jusqu’au clic** ![Exécuter jusqu’au clic](../../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    L’utilisation de ce bouton revient à définir un point d’arrêt temporaire. **Exécuter jusqu’au clic** est pratique pour examiner rapidement une zone visible du code d’application (vous pouvez cliquer dans n’importe quel fichier ouvert).

    Le débogueur avance jusqu’à l’implémentation de la méthode `Console.WriteLine` pour la classe `Triangle`.

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

     Vous devez normalement être revenu dans la boucle `foreach` de la méthode `Main`.

## <a name="restart-your-app-quickly"></a>Redémarrer rapidement votre application

Cliquez sur le bouton **Redémarrer** ![Redémarrer l’application](../../debugger/media/dbg-tour-restart.png "RestartApp") dans la barre d’outils Débogage (**Ctrl** + **Maj**  + **F5**).

Quand vous appuyez sur **Redémarrer**, vous gagnez du temps par rapport à l’action consistant à arrêter l’application, puis à redémarrer le débogueur. Le débogueur se met en pause sur le premier point d’arrêt qui est atteint par l’exécution du code.

Le débogueur s’arrête à nouveau au niveau du point d’arrêt que vous définissez, à la méthode `shape.Draw()`.

## <a name="inspect-variables-with-data-tips"></a>Inspecter des variables avec des bulles d’informations (datatips)

Les fonctionnalités qui vous permettent d’inspecter des variables sont parmi les plus pratiques du débogueur : vous pouvez faire cela de différentes façons. Souvent, quand vous essayez de déboguer un problème, vous essayez de déterminer si les variables stockent les valeurs que vous prévoyez à un moment donné.

1. Alors que l’exécution est mise en pause sur la méthode `shape.Draw()`, placez le curseur sur l’objet `shape`. Vous voyez alors sa valeur de propriété par défaut, le type d’objet `Rectangle`.

1. Développez l’objet `shape` pour voir toutes ses propriétés (notamment la propriété `Height`, qui a la valeur 0).

1. Appuyez plusieurs fois sur **F10** (ou choisissez **Déboguer** > **Pas à pas principal**) pour itérer une fois la boucle `foreach`, en effectuant à nouveau une pause sur `shape.Draw()`.

1. Placez une nouvelle fois le curseur sur l’objet shape. Cette fois-ci, vous voyez un nouvel objet de type `Triangle`.

     ![Afficher une bulle d’informations](../csharp/media/get-started-data-tip.gif "Afficher une bulle d’informations")

    Souvent, lors du débogage, vous voulez un moyen rapide de vérifier les valeurs des propriétés sur des variables pour voir si elles stockent bien les valeurs prévues. Les bulles d’informations (« data tips ») sont un bon moyen de le faire.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Inspecter des variables avec les Fenêtres Automatique et Variables locales

1. Examinez la fenêtre **Automatique** en bas de l’éditeur de code.

    Si elle est fermée, ouvrez-la pendant que l’exécution est mise en pause dans le débogueur en choisissant **Déboguer** > **Windows** > **Automatique**.

1. Développez l’objet `shapes`.

     ![Inspecter des variables dans la fenêtre Automatique](../csharp/media/get-started-autos-window.png "Fenêtre Automatique")

    Dans la fenêtre **Automatique**, vous voyez des variables et leur valeur actuelle. La fenêtre **Automatique** montre toutes les variables utilisées dans la ligne active ou la ligne précédente (consultez la documentation pour les comportements selon le langage).

1. Ensuite, examinons la fenêtre **Variables locales**, sous un onglet à côté de la fenêtre **Automatique**.

    La fenêtre **Variables locales** montre les variables qui se trouvent dans l’[étendue](https://www.wikipedia.org/wiki/Scope_(computer_science)) actuelle, c’est-à-dire le contexte d’exécution actif.

## <a name="set-a-watch"></a>Définir un espion

1. Dans la fenêtre principale de l’éditeur de code, cliquez sur l’objet `shapes` et choisissez **Ajouter un espion**.

    La fenêtre **Espion** s’ouvre en bas de l’éditeur de code. Vous pouvez utiliser une fenêtre **Espion** pour spécifier une variable (ou une expression) que vous voulez observer.

    Vous avez maintenant un espion défini sur l’objet `shapes` et vous pouvez voir sa valeur changer au fil de votre déplacement dans le débogueur. Contrairement à d’autres fenêtres de variables, la fenêtre **Espion** montre toujours les variables que vous observez (elles apparaissent en grisé quand elles sont en dehors de l’étendue).

## <a name="examine-the-call-stack"></a>Examiner la pile des appels

1. Alors que l’exécution est mise en pause dans la boucle `foreach`, cliquez sur la fenêtre **Pile des appels** qui est ouverte par défaut dans le volet inférieur droit.

    Si elle est fermée, ouvrez-la pendant que l’exécution est mise en pause dans le débogueur en choisissant **Déboguer** > **Windows** > **Pile des appels**.

2. Appuyez plusieurs fois sur **F11** jusqu’à ce que le débogueur fasse une pause dans la méthode `Base.Draw` de la classe `Triangle` dans l’éditeur de code. Regardez la fenêtre **Pile des appels**.

    ![Examiner la pile des appels](../csharp/media/get-started-call-stack.png "ExamineCallStack")

    La fenêtre **Pile des appels** montre l’ordre dans lequel les méthodes et les fonctions sont appelées. La ligne du haut montre la fonction active (méthode `Triangle.Draw` dans cette application). La deuxième ligne montre que `Triangle.Draw` a été appelée à partir de la méthode `Main`, etc.

   > [!NOTE]
   > La fenêtre **Pile des appels** est similaire à la perspective Débogage dans certains IDE, comme Eclipse.

    La pile des appels est un bon moyen d’examiner et de comprendre le flux d’exécution d’une application.

    Vous pouvez double-cliquer sur une ligne de code pour accéder à ce code source ; ceci change également l’étendue active inspectée par le débogueur. Cette action ne fait pas avancer le débogueur.

    Vous pouvez également utiliser les menus contextuels de la fenêtre **Pile des appels** pour faire d’autres choses. Par exemple, vous pouvez insérer des points d’arrêt dans des fonctions spécifiées, faire avancer le débogueur avec **Exécuter jusqu’au curseur** et aller examiner le code source. Pour plus d'informations, voir [Procédure : examiner la pile des appels](../../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Changer le flux d’exécution

1. Alors que le débogueur est mis en pause dans l’appel de la méthode `Circle.Draw`, utilisez la souris pour sélectionner la flèche jaune (pointeur d’exécution) sur la gauche, puis déplacez la flèche jaune d’une ligne vers le haut, où est fait l’appel de la méthode `Console.WriteLine`.

1. Appuyez sur **F11**.

    Le débogueur réexécute la méthode `Console.WriteLine` (vous voyez ceci dans la sortie de la fenêtre de console).

    En changeant le flux d’exécution, vous pouvez effectuer des opérations comme tester d’autres chemins d’exécution du code ou réexécuter du code sans devoir redémarrer le débogueur.

    > [!WARNING]
    > Vous devez rester prudent avec cette fonctionnalité, vous pouvez voir un avertissement dans l’info-bulle. Vous pouvez aussi en voir d’autres. Le fait de déplacer le pointeur ne peut pas rétablir votre application à un état antérieur.

1. Appuyez sur **F5** pour poursuivre l’exécution de l’application.

    Félicitations ! Vous avez terminé ce didacticiel.

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez découvert comment démarrer le débogueur, parcourir le code pas à pas et inspecter des variables. Vous pouvez obtenir une présentation générale des fonctionnalités du débogueur et suivre des liens qui donnent accès à plus d’informations.

> [!div class="nextstepaction"]
> [Présentation du débogueur](../../debugger/debugger-feature-tour.md)
