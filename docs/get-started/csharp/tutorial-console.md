---
title: 'Tutoriel : Bien démarrer avec des applications console C#'
description: Découvrez comment créer une application console C# dans Visual Studio, étape par étape.
ms.custom: seodec18, get-started
ms.date: 12/12/2018
ms.technology: vs-ide-general
ms.prod: visual-studio-dev15
ms.topic: tutorial
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 333eeb3f826663d979e1cec444ede7eda4b55b2a
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2018
ms.locfileid: "53562215"
---
# <a name="tutorial-get-started-with-a-c-console-app-in-visual-studio"></a>Tutoriel : Bien démarrer avec une application console C# dans Visual Studio

Dans ce tutoriel pour C# vous allez utiliser Visual Studio afin de créer et d’exécuter une application console tout en explorant certaines fonctionnalités de [l’environnement de développement intégré (IDE) Visual Studio](../visual-studio-ide.md).

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) pour l’installer gratuitement.

## <a name="create-a-project"></a>Créer un projet

Commençons par créer un projet d’application C#. Le type de projet inclut tous les fichiers de modèle dont vous aurez besoin au départ.

1. Ouvrez Visual Studio 2017.

2. Dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet**.

3. Dans le volet gauche de la boîte de dialogue **Nouveau projet**, développez **C#**, puis choisissez **.NET Core**. Dans le volet central, choisissez **Application console (.NET Core)**. Ensuite, nommez le fichier *Calculator*.

   ![Modèle de projet d’application console (.NET Core) dans la boîte de dialogue Nouveau projet dans l’IDE de Visual Studio](./media/new-project-csharp-calculator-console-app.png)

### <a name="add-a-workgroup-optional"></a>Ajouter un groupe de travail (facultatif)

Si vous ne voyez pas le modèle de projet **Application console (.NET Core)**, vous pouvez l’obtenir en ajoutant la charge de travail **Développement multiplateforme .NET Core**. Pour savoir comment procéder, consultez la section « [Qu’est-ce qu’une charge de travail et comment en ajouter une ?](#workload) » dans le Forum aux questions.

## <a name="create-the-app"></a>Créer l’application

Tout d’abord, nous allons ajouter le code pour créer une calculatrice de base. Ensuite, nous allons modifier le code pour ajouter des fonctionnalités. Après cela, nous allons déboguer l’application pour rechercher et corriger les erreurs. Enfin, nous allons affiner le code pour rendre plus efficace.

Commençons par ajouter le code de la calculatrice de base à votre projet.

1. Dans l’éditeur de code, supprimez le code « Hello World » par défaut.

    ![Supprimer le code Hello World par défaut de votre nouvelle application de calculatrice](./media/csharp-console-calculator-deletehelloworld.png)

   Plus précisément, supprimez tout le code que vous voyez dans l’éditeur de code.

1. Entrez ou collez le nouveau code suivant dans l’éditeur de code :

    ```csharp
    using System;

    namespace Calculator
    {
        class Program
        {
            static void Main(string[] args)
            {
                // Declare variables and then initialize to zero
                int num1 = 0; int num2 = 0;

                // Display title as the C# console calculator app
                Console.WriteLine("Console Calculator in C#\r");
                Console.WriteLine("------------------------\n");

                // Ask the user to type the first number
                Console.WriteLine("Type a number, and then press Enter");
                num1 = Convert.ToInt32(Console.ReadLine());

                // Ask the user to type the second number
                Console.WriteLine("Type another number, and then press Enter");
                num2 = Convert.ToInt32(Console.ReadLine());

                // Ask the user to choose an option
                Console.WriteLine("Choose an option from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                // Use a switch statement to do the math
                switch (Console.ReadLine())
                {
                    case "a":
                        Console.WriteLine($"Your result: {num1} + {num2} = " + (num1 + num2));
                        break;
                    case "s":
                        Console.WriteLine($"Your result: {num1} - {num2} = " + (num1 - num2));
                        break;
                    case "m":
                        Console.WriteLine($"Your result: {num1} * {num2} = " + (num1 * num2));
                        break;
                    case "d":
                        Console.WriteLine($"Your result: {num1} / {num2} = " + (num1 / num2));
                        break;
                }
                // Wait for the user to respond before closing
                Console.Write("Press any key to close the Calculator console app...");
                Console.ReadKey();
            }
        }
    }
    ```
1. Cliquez sur **Calculator** pour exécuter votre programme, ou appuyez sur **F5**.

   ![Cliquer sur le bouton Calculator pour exécuter l’application à partir de la barre d’outils](./media/csharp-console-calculator-button.png)

   Une fenêtre de console s'ouvre.

1. Affichez votre application dans la fenêtre de console, puis suivez les invites pour ajouter les chiffres **42** et **119**.

   Votre application doit ressembler à la capture d’écran suivante :

    ![Fenêtre de console montrant l’application Calculator, avec des invites sur les actions à effectuer](./media/csharp-console-calculator.png)

### <a name="add-decimals"></a>Ajouter des nombres décimaux

Actuellement, l’application Calculator accepte et retourne des nombres entiers. Toutefois, elle sera plus précise si nous ajoutons le code permettant les nombres décimaux.

Comme dans la capture d’écran suivante, si vous exécutez l’application et divisez 42 par 119, votre résultat est 0 (zéro), ce qui n’est pas exact.

![Fenêtre de console montrant l’application Calculator qui ne retourne pas un nombre décimal en tant que résultat](./media/csharp-console-calculator-nodecimal.png)

Corrigeons le code afin qu’il gère les nombres décimaux.

1. Remplacez chaque instance de la variable `int` par `float`.

   (Vous pouvez utiliser la commande [Rechercher et remplacer](../../ide/finding-and-replacing-text.md#find-and-replace-control) pour vous aider dans cette tâche. Pour accéder à la commande de recherche au sein de l’éditeur de code, appuyez sur **Crtl**+**F**. Ensuite, choisissez le bouton **Suivant** ou le bouton **Précédent** dans la commande de recherche. Pour accéder aux options de remplacement, choisissez le bouton en regard de la zone de texte **Rechercher**. Pour effectuer un remplacement à la fois, choisissez le bouton **Suivant** en regard de la zone de texte **Remplacer**. Pour remplacer toutes les occurrences en une seule fois, choisissez le bouton **Remplacer tout**.)

1. Exécutez à nouveau votre application de calculatrice et divisez **42** par **119**.

   Notez que l’application retourne désormais un chiffre décimal au lieu de zéro.

    ![Fenêtre de console montrant l’application Calculator qui retourne maintenant un nombre décimal en tant que résultat](./media/csharp-console-calculator-decimal.png)

Toutefois, l’application ne produit qu’un résultat décimal. Apportons quelques ajustements au code afin que l’application puisse aussi calculer des valeurs décimales.

1. Remplacez chaque instance de la variable `float` par `double`.

1. Remplacez chaque instance de la méthode `Convert.ToInt32` par `Convert.ToDouble`.

1. Exécutez votre application de calculatrice et divisez **42,5** par **119,75**.

   Notez que l’application accepte maintenant les valeurs décimales et retourne un chiffre décimal plus long comme résultat.

    ![Fenêtre de console montrant l’application Calculator qui accepte maintenant les nombres décimaux et retourne un nombre décimal plus long en tant que résultat](./media/csharp-console-calculator-usedecimals.png)

    (Nous corrigerons le nombre de décimales dans la section [Réviser le code](#revise-the-code).)

## <a name="debug-the-app"></a>Déboguer l’application

Nous avons amélioré notre application de calculatrice de base, mais elle ne dispose pas encore des filets de sécurité pour gérer les exceptions, telles que les erreurs d’entrée utilisateur.

Par exemple, si vous essayez de diviser un nombre par zéro, ou entrez un caractère alphabétique lorsque l’application attend un caractère numérique (ou vice versa), l’application cesse de fonctionner et retourne une erreur.

Nous allons passer en revue quelques erreurs d’entrée utilisateur courantes, les rechercher dans le [débogueur](../../debugger/debugger-feature-tour.md) et les corriger dans le code.

### <a name="fix-the-divide-by-zero-error"></a>Corriger l’erreur de division par zéro

Lorsque vous essayez de diviser un nombre par zéro, l’application console se bloque. Visual Studio vous montre alors ce qui est incorrect dans l’éditeur de code.

   ![L’éditeur de code Visual Studio affiche l’erreur de division par zéro](./media/csharp-console-calculator-dividebyzero-error.png)

Nous allons modifier le code pour gérer cette erreur.

1. Supprimez le code qui s’affiche directement entre `case "d":` et le commentaire indiquant `// Wait for the user to respond before closing`.

1. Remplacez-le par le code suivant :

   ```csharp
            // Ask the user to enter a non-zero divisor until they do so
                while (num2 == 0)
                {
                    Console.WriteLine("Enter a non-zero divisor: ");
                    num2 = Convert.ToInt32(Console.ReadLine());
                }
                Console.WriteLine($"Your result: {num1} / {num2} = " + (num1 / num2));
                break;
        }
    ```

   Une fois que vous ajoutez le code, la section avec l’instruction `switch` doit ressembler à la capture d’écran suivante :

   ![La section « commutateur » modifiée dans l’éditeur de code Visual Studio](./media/csharp-console-calculator-switch-code.png)

Maintenant, quand vous divisez n’importe quel nombre par zéro, l’application vous demande un autre nombre. Encore mieux : Elle ne s’arrêtera pas de demander jusqu'à ce que vous fournissiez un nombre différent de zéro.

   ![L’éditeur de code Visual Studio affiche l’erreur de division par zéro](./media/csharp-console-calculator-dividebyzero.png)

### <a name="fix-the-format-error"></a>Corriger l’erreur de « format »

Si vous entrez un caractère alphabétique lorsque l’application attend un caractère numérique (ou vice versa), l’application de console se bloque. Visual Studio vous montre alors ce qui est incorrect dans l’éditeur de code.

   ![L’éditeur de code Visual Studio affiche une erreur de format](./media/csharp-console-calculator-format-error.png)

Pour corriger cette erreur, nous devons refactoriser le code que nous avons précédemment entré.

#### <a name="revise-the-code"></a>Réviser le code

Plutôt que de nous appuyer sur la classe `program` pour gérer tout le code, nous allons diviser notre application de deux classes : `calculator` et `program`.  

La classe `calculator` gérera le gros du travail de calcul et la classe `program` gèrera l’interface utilisateur et le travail de capture d’erreur.

Allons-y.

1. Supprimez tout ce qui se situe *après* le bloc de code suivant :

    ```csharp

    using System;

    namespace Calculator
    {

    ```

1. Ensuite, ajoutez une nouvelle classe `calculator`, comme suit :

    ```csharp
    class Calculator
    {
        public static double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error

            // Use a switch statement to do the math
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    break;
                case "s":
                    result = num1 - num2;
                    break;
                case "m":
                    result = num1 * num2;
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                    }
                    break;
                // Return text for an incorrect option entry
                default:
                    break;
            }
            return result;
        }
    }

    ```

1. Puis, ajoutez une nouvelle classe `program`, comme suit :

    ```csharp
    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            while (!endApp)
            {
                // Declare variables and set to empty
                string numInput1 = "";
                string numInput2 = "";
                double result = 0;

                // Ask the user to type the first number
                Console.Write("Type a number, and then press Enter: ");
                numInput1 = Console.ReadLine();

                double cleanNum1 = 0;
                while (!double.TryParse(numInput1, out cleanNum1))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput1 = Console.ReadLine();
                }

                // Ask the user to type the second number
                Console.Write("Type another number, and then press Enter: ");
                numInput2 = Console.ReadLine();

                double cleanNum2 = 0;
                while (!double.TryParse(numInput2, out cleanNum2))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput2 = Console.ReadLine();
                }

                // Ask the user to choose an operator
                Console.WriteLine("Choose an operator from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                string op = Console.ReadLine();

                try
                {
                    result = Calculator.DoOperation(cleanNum1, cleanNum2, op);
                    if (double.IsNaN(result))
                    {
                        Console.WriteLine("This operation will result in a mathematical error.\n");
                    }
                    else Console.WriteLine("Your result: {0:0.##}\n", result);
                }
                catch (Exception e)
                {
                    Console.WriteLine("Oh no! An exception occurred trying to do the math.\n - Details: " + e.Message);
                }

                Console.WriteLine("------------------------\n");

                // Wait for the user to respond before closing
                Console.Write("Press 'n' and Enter to close the app, or press any other key and Enter to continue: ");
                if (Console.ReadLine() == "n") endApp = true;

                Console.WriteLine("\n"); // Friendly linespacing
            }
            return;
        }
    }
    ```
1. Cliquez sur **Calculator** pour exécuter votre programme, ou appuyez sur **F5**.

1. Suivez les invites et divisez le nombre **42** par le nombre **119**. Votre application doit se présenter comme suit :

    ![Fenêtre de console montrant l’application Calculator refactorisée qui comprend des invites sur les actions à entreprendre et la gestion des erreurs pour les entrées incorrectes](./media/csharp-console-calculator-refactored.png)

    Notez que vous avez la possibilité d’entrer plus d’équations jusqu'à ce que vous choisissiez de fermer l’application de console. Et nous avons également réduit le nombre de décimales dans le résultat.

## <a name="close-the-app"></a>Fermer l’application

1. Si ce n’est déjà fait, fermez l’application de calculatrice.

1. Fermez le volet **Sortie** dans Visual Studio.

   ![Fermer le volet Sortie dans Visual Studio](./media/csharp-calculator-close-output-pane.png)

1. Dans Visual Studio, appuyez sur **Ctrl**+**S** pour enregistrer votre application.

1. Fermez Visual Studio.

## <a name="code-complete"></a>Code terminé

Au cours de ce tutoriel, nous avons apporté de nombreuses modifications à l’application de calculatrice. L’application gère désormais plus efficacement les ressources de calcul, ainsi que la plupart des erreurs d’entrée utilisateur.

Voici le code complet, au même endroit :

```csharp

using System;

namespace Calculator
{
    class Calculator
    {
        public static double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error

            // Use a switch statement to do the math
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    break;
                case "s":
                    result = num1 - num2;
                    break;
                case "m":
                    result = num1 * num2;
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                    }
                    break;
                // Return text for an incorrect option entry
                default:
                    break;
            }
            return result;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            while (!endApp)
            {
                // Declare variables and set to empty
                string numInput1 = "";
                string numInput2 = "";
                double result = 0;

                // Ask the user to type the first number
                Console.Write("Type a number, and then press Enter: ");
                numInput1 = Console.ReadLine();

                double cleanNum1 = 0;
                while (!double.TryParse(numInput1, out cleanNum1))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput1 = Console.ReadLine();
                }

                // Ask the user to type the second number
                Console.Write("Type another number, and then press Enter: ");
                numInput2 = Console.ReadLine();

                double cleanNum2 = 0;
                while (!double.TryParse(numInput2, out cleanNum2))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput2 = Console.ReadLine();
                }

                // Ask the user to choose an operator
                Console.WriteLine("Choose an operator from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                string op = Console.ReadLine();

                try
                {
                    result = Calculator.DoOperation(cleanNum1, cleanNum2, op);
                    if (double.IsNaN(result))
                    {
                        Console.WriteLine("This operation will result in a mathematical error.\n");
                    }
                    else Console.WriteLine("Your result: {0:0.##}\n", result);
                }
                catch (Exception e)
                {
                    Console.WriteLine("Oh no! An exception occurred trying to do the math.\n - Details: " + e.Message);
                }

                Console.WriteLine("------------------------\n");

                // Wait for the user to respond before closing
                Console.Write("Press 'n' and Enter to close the app, or press any other key and Enter to continue: ");
                if (Console.ReadLine() == "n") endApp = true;

                Console.WriteLine("\n"); // Friendly linespacing
            }
            return;
        }
    }
}

```

## <a name="quick-answers-faq"></a>Questions fréquentes (FAQ) et réponses rapides

Voici des Questions fréquentes (FAQ) rapides pour mettre en lumière certains concepts clés. Le Forum aux questions inclut également des réponses aux questions qui peuvent survenir lorsque vous suivez les procédures décrites dans le tutoriel.

### <a name="what-is-c"></a>Qu’est-ce que C# ?

C# est un langage de programmation de type sécurisé qui s’exécute sur .NET Framework et .NET Core. Avec C#, vous pouvez créer des applications Windows, des applications client-serveur, des applications de base de données, des services web XML, des composants distribués et bien plus encore.

### <a name="what-is-visual-studio"></a>Qu’est-ce que Visual Studio ?

Visual Studio est une suite de développement intégrée d’outils de productivité pour les développeurs. Il s’agit d’un programme qui sert à créer des applications et des programmes.

### <a name="what-is-a-console-app"></a>Qu’est-ce qu’une application console ?

Une application console prend une entrée et affiche la sortie dans une fenêtre de ligne de commande, également appelée console.

### <a name="what-is-net-core"></a>Qu'est-ce que le .NET Core ?

.NET Core est la suite logique du .NET Framework. Là où le .NET Framework vous permettait de partager du code entre les langages de programmation, .NET Core ajoute la capacité à partager du code entre des plateformes. De plus, il est open source.

(.NET Framework et .NET Core comportent des bibliothèques de fonctionnalités prégénérées, ainsi qu’un common language runtime (CLR) qui fonctionne comme une machine virtuelle sur laquelle votre code s’exécute.)

### <a id="workload"></a>Qu’est-ce qu’une charge de travail et comment en ajouter une ?

Une charge de travail dans Visual Studio représente un ensemble d’options de programmation et de modèles que vous pouvez utiliser pour personnaliser votre installation de Visual Studio. Une charge de travail installe uniquement les outils dont vous avez besoin pour le langage de programmation et la plateforme de votre choix. Voici comment les installer.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Option 1 : Utiliser la boîte de dialogue Nouveau projet

1. Cliquez sur le lien **Ouvrir Visual Studio Installer** dans le volet gauche de la boîte de dialogue **Nouveau projet**.

   ![Cliquer sur le lien Ouvrir Visual Studio Installer dans la boîte de dialogue Nouveau projet](./media/csharp-open-visual-studio-installer-generic-dark.png)

1. Visual Studio Installer est lancé. Choisissez la charge de travail **Développement multiplateforme .NET Core**, puis choisissez **Modifier**.

   ![Charge de travail Développement multiplateforme .Net Core dans Visual Studio Installer](./media/dot-net-core-xplat-dev-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Option 2 : Utiliser la barre de menus Outils

1. Quittez la boîte de dialogue **Nouveau projet** puis, dans la barre de menus supérieure, choisissez **Outils** > **Obtenir les outils et fonctionnalités**.

1. Visual Studio Installer est lancé. Choisissez la charge de travail **Développement multiplateforme .NET Core**, puis choisissez **Modifier**.

## <a name="next-steps"></a>Étapes suivantes

Félicitations ! Vous avez terminé ce didacticiel. Pour plus d’informations, passez aux tutoriels suivants.

> [!div class="nextstepaction"]
> [Tutoriels C#](/dotnet/csharp/tutorials/)

## <a name="see-also"></a>Voir aussi

* [Cours vidéo Concepts de base de C# pour les débutants](https://mva.microsoft.com/en-us/training-courses/c-fundamentals-for-absolute-beginners-16169)