---
title: Apprenez à déboguer à l’aide du débogueur Visual Studio
ms.description: Learn how to start the Visual Studio debugger, step through code, and inspect data.
ms.custom: mvc
ms.date: 08/01/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- CSharp
- C++
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8717c8f4c9d4bae12acf576620368b4aac64a185
ms.sourcegitcommit: 4708f0ba09b540424efcc344f8438f25432e3d51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44384225"
---
# <a name="tutorial-learn-to-debug-using-visual-studio"></a>Didacticiel : Apprenez à déboguer à l’aide de Visual Studio

Cet article présente les fonctionnalités du débogueur Visual Studio dans une procédure pas à pas. Si vous souhaitez une vue plus générale des fonctionnalités du débogueur, consultez [visite guidée des fonctionnalités débogueur](../debugger/debugger-feature-tour.md). Lorsque vous *déboguer votre application*, cela signifie généralement que vous exécutez votre application avec le débogueur attaché. Lorsque vous effectuez cette opération, le débogueur fournit de nombreuses façons de voir ce que fait votre code pendant son exécution. Vous pouvez parcourir votre code et examinez les valeurs stockées dans des variables, vous pouvez définir des observations sur les variables pour voir quand les valeurs changent, vous pouvez examiner le chemin d’accès de l’exécution de votre code, si une branche de code est en cours d’exécution, et ainsi de suite. S’il s’agit de la première fois que vous avez essayé de déboguer du code, il pouvez que vous souhaitez lire [débogage pour les débutants](../debugger/debugging-absolute-beginners.md) avant de poursuivre cet article.

|         |         |
|---------|---------|
|  ![Icône représentant une caméra pour les vidéos](../install/media/video-icon.png "Regarder une vidéo")  |    [Regardez une vidéo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugger-Feature-tour-of-Visual-studio-2017-sqwiwLD6D_1111787171) sur le débogage, qui affiche des étapes similaires. |

Bien que l’application de démonstration est c# et C++, les fonctionnalités sont applicables à Visual Basic, JavaScript et d’autres langages pris en charge par Visual Studio (sauf indication contraire). Les captures d’écran sont en c#. Pour basculer entre le code c# et C++ exemple dans cet article, utilisez le filtre de langage dans le coin supérieur droit de cette page.

Dans ce didacticiel, vous allez effectuer les actions suivantes :

> [!div class="checklist"]
> * Démarrez le débogueur et les points d’arrêt.
> * Découvrez les commandes pour parcourir le code dans le débogueur
> * Inspecter des variables dans des bulles d’informations et les fenêtres du débogueur
> * Examiner la pile des appels

## <a name="prerequisites"></a>Prérequis

* Vous devez disposer de Visual Studio 2017 est installé et le **développement .NET desktop** ou **développement Desktop en C++** charge de travail.

    Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) pour l’installer gratuitement.

    Si vous devez installer la charge de travail mais que vous avez déjà Visual Studio, cliquez sur le lien **Ouvrir Visual Studio Installer** dans le volet gauche de la boîte de dialogue **Nouveau projet** (sélectionnez **Fichier** > **Nouveau** > **Projet**). Visual Studio Installer est lancé. Choisissez le. **Développement bureautique NET** ou **développement Desktop en C++** charge de travail, puis choisissez **modifier**.

## <a name="create-a-project"></a>Créer un projet

1. Dans Visual Studio, sélectionnez **Fichier > Nouveau projet**.

2. Sous **Visual C#** ou **Visual C++**, choisissez **Windows Desktop**, puis, dans le volet central, choisissez **application Console** ( **Application de Console Windows** en C++).

    Si vous ne voyez pas le **Application Console** modèle de projet, cliquez sur le **ouvrir Visual Studio Installer** lien dans le volet gauche de la **nouveau projet** boîte de dialogue. Visual Studio Installer est lancé. Choisissez le *développement .NET desktop** ou **développement Desktop en C++** charge de travail, puis choisissez **modifier**.

3. Tapez un nom tel que **get-démarré-débogage** et cliquez sur **OK**.

    Visual Studio crée le projet.

4. Dans *Program.cs* (c#) ou *get-démarré-debugging.cpp* (C++), remplacez le code suivant

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

    ```c++
    int main()
    {
        return 0;
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

    ```c++
    #include "pch.h"

    #include <string>
    #include <vector>
    #include <iostream>

    class Shape
    {
        int privateX = 0;
        int privateY = 0;
        int privateHeight = 0;
        int privateWidth = 0;

        int getX() const { return privateX; }
        void setX(int value) { privateX = value; }

        int getY() const { return privateY; }
        void setY(int value) { privateY = value; }

        int getHeight() const { return privateHeight; }
        void setHeight(int value) { privateHeight = value; }

        int getWidth() const { return privateWidth; }
        void setWidth(int value) { privateWidth = value; }

        public:
        // Virtual method
        virtual void Draw()
        {
            std::wcout << L"Performing base class drawing tasks" << std::endl;
        }
    };

    class Circle : public Shape
    {
        public:
        void Draw() override
        {
        // Code to draw a circle...
        std::wcout << L"Drawing a circle" << std::endl;
        Shape::Draw();
        }
    };

    class Rectangle : public Shape
    {
        public:
        void Draw() override
        {
        // Code to draw a rectangle...
        std::wcout << L"Drawing a rectangle" << std::endl;
        Shape::Draw();
        }
    };

    class Triangle : public Shape
    {
        public:
        void Draw() override
        {
        // Code to draw a triangle...
        std::wcout << L"Drawing a trangle" << std::endl;
        Shape::Draw();
        }
    };

    int main(std::vector<std::wstring> &args)
    {
        auto shapes = std::vector<Shape*>
        {
            new Rectangle(),
            new Triangle(),
            new Circle()
        };

        for (auto shape : shapes)
        {
            shape->Draw();
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

1. Appuyez sur **F5** (**Déboguer > Démarrer le débogage**) ou le **démarrer le débogage** bouton ![démarrer le débogage](../debugger/media/dbg-tour-start-debugging.png "démarrer le débogage ") dans la barre d’outils de débogage.

     **F5** démarre l’application avec le débogueur est attachée à l’application traiter, mais actuellement, nous n’avons pas fait rien de spécial à examiner le code. Par conséquent, l’application se charge juste et vous voyez la sortie de console.

    ```
    Drawing a rectangle
    Performing base class drawing tasks
    Drawing a triangle
    Performing base class drawing tasks
    Drawing a circle
    Performing base class drawing tasks
    ```

     Dans ce didacticiel, nous examinons plus en détail cette application à l’aide du débogueur et avoir une idée du débogueur de fonctionnalités.

2. Arrêtez le débogueur en appuyant sur le taquet rouge ![arrêter le débogage](../debugger/media/dbg-tour-stop-debugging.png "arrêter le débogage") bouton.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Définissez un point d’arrêt et démarrez le débogueur

1. Dans le `foreach` boucle de la `Main` (fonction) (`for` boucle en C++ `main` fonction), définissez un point d’arrêt en cliquant sur la marge gauche de la ligne de code suivante :

    `shape.Draw()` (ou, `shape->Draw()` dans C++)

    Un cercle rouge s’affiche où vous avez défini le point d’arrêt.

    Les points d'arrêt constituent une fonctionnalité élémentaire et essentielle de toute procédure de débogage fiable. Quand vous définissez un point d'arrêt, Visual Studio interrompt l'exécution du code à l'emplacement du point d'arrêt pour vous permettre d'examiner les valeurs des variables, le comportement de la mémoire ou encore la bonne exécution ou non d'une branche de code. 

6. Appuyez sur **F5** ou **démarrer le débogage** bouton, l’application démarre, et le débogueur exécute jusqu'à la ligne de code où vous avez défini le point d’arrêt.

    ![Définir et atteindre un point d’arrêt](../debugger/media/get-started-set-breakpoint.gif)

    La flèche jaune représente l’instruction sur laquelle le débogueur a suspendu, ce qui interrompt également l’exécution d’application au même moment (cette instruction n’a pas encore exécuté).

     Si l’application n’est pas encore en cours d’exécution, **F5** démarre le débogueur et s’arrête au premier point d’arrêt. Sinon, **F5** continue l’exécution de l’application au point d’arrêt suivant.

    Les points d’arrêt sont une fonctionnalité utile quand vous savez quelle ligne ou section de code vous voulez examiner en détail.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Parcourir le code dans le débogueur à l’aide des commandes de l’étape

Principalement, nous utilisons ici, des raccourcis clavier, car c’est un bon moyen pour obtenir rapidement à l’exécution de votre application dans le débogueur (commandes équivalentes tels que menu commandes sont affichées entre parenthèses).

1. Pendant la suspension dans le `shape.Draw` appel de méthode dans le `Main` (méthode) (`shape->Draw` en C++), appuyez sur **F11** (ou choisissez **Déboguer > pas à pas détaillé**) pour faire avancer dans le code pour le `Rectangle` classe.

     ![Utilisez F11 pour le code pas à pas détaillé](../debugger/media/get-started-f11.png "détaillé F11")

     F11 est la commande **pas à pas détaillé** et elle exécute l'application une instruction à la fois. F11 est une bonne solution pour examiner le flux d’exécution en détails. (Pour déplacer plus rapidement le code, nous vous montrons d’autres options également.) Par défaut, le débogueur ignore le code non-utilisateur (si vous souhaitez plus d’informations, consultez [uniquement mon Code](../debugger/just-my-code.md)).

2. Appuyez sur **F10** (ou choisissez **Déboguer > pas à pas principal**) plusieurs fois jusqu'à ce que le débogueur s’arrête sur la `base.Draw` appel de méthode (`Shape::Draw` en C++), puis appuyez sur **F10** Encore une fois.

     ![Utiliser la touche F10 pour le code pas à pas principal](../debugger/media/get-started-step-over.png "F10 pas à pas principal")

     Notez que cette fois que le débogueur ne parcourt pas le `Draw` méthode de la classe de base (`Shape`). **F10** fait avancer le débogueur sans entrer dans les fonctions ou méthodes dans votre code d’application (le code s’exécute toujours). En appuyant sur F10 le `base.Draw` (ou `Shape::Draw`) appel de méthode (au lieu de **F11**), nous avons ignoré sur le code d’implémentation pour `base.Draw` (qui nous n’allons pas maintenant intéressés par exemple).

## <a name="navigate-code-using-run-to-click"></a>Parcourir le code à l’aide d’exécution sur clic

5. Dans l’éditeur de code, faites défiler vers le bas et placez le curseur sur le `Console.WriteLine` (méthode) (`std::cout` en C++) dans le `Triangle` classe jusqu'à ce que le vert **exécuter jusqu’au clic** bouton ![exécuter jusqu’au clic](../debugger/media/dbg-tour-run-to-click.png " RunToClick") apparaît à gauche.

     ![Utiliser l’exécution sur clic fonctionnalité](../debugger/media/get-started-run-to-click.png "exécuter jusqu’au clic")

    >  [!NOTE]
    > Le **exécuter jusqu’au clic** bouton est une nouveauté de [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]. Si vous ne voyez pas le bouton fléché vert, utilisez **F11** dans cet exemple à la place pour faire avancer le débogueur au bon endroit.

6. Cliquez sur le **exécuter jusqu’au clic** bouton ![exécuter jusqu’au clic](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    L’utilisation de ce bouton est similaire à la définition d’un point d’arrêt temporaire. **Exécuter jusqu’au clic** est pratique pour la navigation rapidement dans une zone visible du code d’application (vous pouvez cliquer dans n’importe quel fichier ouvrir).

    Le débogueur avance à la `Console.WriteLine` implémentation de méthode pour le `Triangle` classe (`std::cout` dans C++).

    Pendant la suspension, vous remarquez une faute de frappe ! La sortie « Dessin un trangle » est mal orthographiée. Nous pouvons corriger ici lors de l’exécution de l’application dans le débogueur.

## <a name="edit-code-and-continue-debugging"></a>Modifier le code et continuer le débogage

1. Cliquez sur « Dessin un trangle » et tapez une correction, en remplaçant « trangle » par « triangle ».

1. Appuyez sur **F11** une seule fois et que vous consultez que le débogueur avance à nouveau.

    > [!NOTE]
    > Selon le type de code que vous modifiez dans le débogueur, vous pouvez voir un message d’avertissement. Dans certains scénarios, le code devra recompiler avant de continuer.

## <a name="step-out"></a>Pas à pas sortant

Supposons que vous avez terminé examinant le `Draw` méthode dans la `Triangle` classe et que vous souhaitez tirer parti de la fonction, mais restent dans le débogueur. Vous pouvez le faire à l’aide de la **pas à pas sortant** commande.

1. Appuyez sur **MAJ** + **F11** (ou **Déboguer > pas à pas sortant**).

     Cette commande reprend l’exécution d’application (et avance le débogueur) jusqu'à ce que retourne la fonction active.

     Vous devez être revenu à la `foreach` boucle dans le `Main` (méthode) (`for` boucle en C++).

## <a name="restart-your-app-quickly"></a>Redémarrez votre application rapidement

Cliquez sur le **redémarrer** ![redémarrer une application](../debugger/media/dbg-tour-restart.png "RestartApp") bouton dans la barre d’outils déboguer (**Ctrl** + **MAJ**   +  **F5**).

Quand vous appuyez sur **redémarrer**, il fait gagner du temps par rapport à l’arrêt de l’application et de redémarrer le débogueur. Le débogueur s’arrête sur le premier point d’arrêt est atteint par l’exécution de code.

Le débogueur s’arrête à nouveau sur le point d’arrêt que vous définissez, sur le `shape.Draw()` (méthode) (`shape->Draw()` en C++).

## <a name="inspect-variables-with-data-tips"></a>Inspecter des variables avec des bulles d’informations

Les fonctionnalités qui vous permettent d’inspecter les variables sont une des fonctionnalités plus utiles du débogueur, et il existe différentes manières de procéder. Souvent, lorsque vous essayez de déboguer un problème, vous essayez de déterminer si les variables sont stocker les valeurs que vous attendez d’avoir à un moment donné.

1. Pendant la suspension sur la `shape.Draw()` (méthode) (`shape->Draw()` en C++), placez le curseur sur le `shapes` objet et que vous consultez sa valeur de propriété par défaut, le `Count` propriété.

1. Développez le `shapes` objet pour voir toutes ses propriétés, telles que le premier index du tableau `[0]`, qui a la valeur de `Rectangle` (c#) ou une adresse mémoire (C++).

     ![Afficher une bulle](../debugger/media/get-started-data-tip.gif "afficher une info-bulle de données")

    Vous pouvez développer davantage les objets pour afficher leurs propriétés, telles que le `Height` propriété du rectangle.

    Souvent, lors du débogage, vous souhaitez un moyen rapide de vérifier les valeurs de propriété sur les objets et les conseils de données constituent un bon moyen de le faire.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Inspecter des variables avec les fenêtres automatique et variables locales

1. Examinez le **automatique** fenêtre en bas de l’éditeur de code.

     ![Inspecter des variables dans la fenêtre automatique](../debugger/media/get-started-autos-window.png "fenêtre automatique")

    Dans le **automatique** fenêtre, vous voyez des variables et leur valeur actuelle. Le **automatique** fenêtre affiche toutes les variables utilisées dans la ligne actuelle ou de la ligne précédente (en C++, la fenêtre affiche les variables dans les trois lignes de code précédents. Consultez la documentation pour le comportement spécifique à la langue).

    > [!NOTE]
    > Dans JavaScript, le **variables locales** fenêtre est pris en charge, mais pas le **automatique** fenêtre.

2. Ensuite, examinons le **variables locales** fenêtre, dans un onglet à côté du **automatique** fenêtre.

    Le **variables locales** fenêtre vous montre les variables qui sont en cours [étendue](https://www.wikipedia.org/wiki/Scope_(computer_science)).

## <a name="set-a-watch"></a>Définir un espion

1. Dans la fenêtre d’éditeur de code principal, cliquez sur le `shapes` de l’objet et choisissez **ajouter un espion**.

    Le **espion** fenêtre s’ouvre au bas de l’éditeur de code. Vous pouvez utiliser un **espion** fenêtre pour spécifier une variable (ou une expression) que vous souhaitez garder un œil sur.

    À présent, vous avez un espion défini sur le `shapes` objet et vous pouvez voir sa valeur changent à mesure que vous parcourez le débogueur. Contrairement à d’autres fenêtres de variables, le **espion** fenêtre affiche toujours les variables que vous surveillez (elles sont grisées lorsque hors de portée).

## <a name="examine-the-call-stack"></a>Examiner la pile des appels

1. Pendant la suspension dans le `foreach` boucle (`for` boucle en C++), cliquez sur le **pile des appels** fenêtre, qui est par défaut ouvert dans le volet inférieur droit.

1. Cliquez sur **F11** plusieurs fois jusqu'à ce que vous voyiez le débogueur suspendre dans le `Circle.Draw` méthode dans l’éditeur de code. Examinez le **pile des appels** fenêtre.

    ![Examiner la pile des appels](../debugger/media/get-started-call-stack.png "ExamineCallStack")

    Le **pile des appels** fenêtre indique l’ordre dans lequel les méthodes et les fonctions sont bien appelées. La première ligne affiche la fonction active (la `Circle.Draw` ou `Circle::Draw` méthode dans cette application). La deuxième ligne montre que `Circle.Draw` a été appelée à partir de la `Main` (méthode) (`main` en C++), et ainsi de suite.

    >  [!NOTE]
    > Le **pile des appels** est identique à la perspective de débogage dans certains IDE comme Eclipse.

    La pile des appels est un bon moyen d’examiner et de comprendre le flux d’exécution d’une application.

    Vous pouvez double-cliquer sur une ligne de code revenir sur ce code source et qui modifie également la portée actuelle est inspectée par le débogueur. Cette action n’avance pas le débogueur.

    Vous pouvez également utiliser les menus contextuels à partir de la **pile des appels** fenêtre pour faire autre chose. Par exemple, vous pouvez insérer des points d’arrêt dans les fonctions spécifiées, faire avancer le débogueur à l’aide de **exécuter jusqu’au curseur**et accédez à examiner le code source. Pour plus d’informations, consultez [Comment : examiner la pile des appels](../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Modifier le flux d’exécution

1. Avec le débogueur en pause dans le `Circle.Draw` appel de méthode, appuyez sur **F11** plusieurs fois jusqu'à ce que le débogueur s’arrête à la `base.Draw` appel de méthode (`Shape::Draw` en C++).

1. Utilisez la souris pour sélectionner la flèche jaune (le pointeur d’exécution) sur la gauche et déplacer la flèche jaune une ligne à la `Console.WriteLine` (`std::cout` en C++) appel de méthode.

1. Appuyez sur **F11** une nouvelle fois.

    Le débogueur réexécute la `Console.WriteLine` (méthode) (`std::cout` en C++).

    En modifiant le flux d’exécution, vous pouvez effectuer des opérations telles que les chemins d’exécution de code différent de test ou de réexécuter le code sans avoir à redémarrer le débogueur.

    > [!WARNING]
    > Souvent, vous devez être prudent avec cette fonctionnalité, et un avertissement s’affiche dans l’info-bulle. Vous pouvez voir les autres avertissements, trop. Déplacer le pointeur ne peut pas rétablir votre application à un état antérieur de l’application.

1. Appuyez sur **F5** pour continuer l’exécution de l’application.

    Félicitations ! Vous avez terminé ce didacticiel.

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris comment démarrer le débogueur, parcourir le code et inspecter les variables. Voulez-vous obtenir une vue d’ensemble des fonctionnalités de débogueur ainsi que des liens vers d’autres informations.

> [!div class="nextstepaction"]
> [Visite guidée des fonctionnalités du débogueur](../debugger/debugger-feature-tour.md)
