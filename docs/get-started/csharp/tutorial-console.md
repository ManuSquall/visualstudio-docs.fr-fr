---
title: 'Tutoriel : Créer une application console C# simple'
description: Découvrez comment créer une application console C# dans Visual Studio, étape par étape.
ms.custom: seodec18, get-started
ms.date: 01/25/2019
ms.technology: vs-ide-general
ms.topic: tutorial
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 79a29fa8b0d512049bf604668d11ea92e2511984
ms.sourcegitcommit: 34940a18f5b03a59567f54c7024a0b16d4272f1e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56156070"
---
# <a name="tutorial-create-a-simple-c-console-app-in-visual-studio"></a>Tutoriel : Créer une application console C# simple dans Visual Studio

Dans ce tutoriel pour C#, vous allez utiliser Visual Studio afin de créer et d’exécuter une application console tout en découvrant certaines fonctionnalités de l’IDE (environnement de développement intégré) Visual Studio.

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) pour l’installer gratuitement.

## <a name="create-a-project"></a>Créer un projet

Commençons par créer un projet d’application C#. Le type de projet inclut tous les fichiers de modèle dont vous aurez besoin au départ.

1. Ouvrez Visual Studio 2017.

2. Dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet**.

3. Dans le volet gauche de la boîte de dialogue **Nouveau projet**, développez **C#**, puis choisissez **.NET Core**. Dans le volet central, choisissez **Application console (.NET Core)**. Ensuite, nommez le fichier *Calculator*.

   ![Modèle de projet d’application console (.NET Core) dans la boîte de dialogue Nouveau projet dans l’IDE de Visual Studio](./media/new-project-csharp-calculator-console-app.png)

### <a name="add-a-workgroup-optional"></a>Ajouter un groupe de travail (facultatif)

Si vous ne voyez pas le modèle de projet **Application console (.NET Core)**, vous pouvez l’obtenir en ajoutant la charge de travail **Développement multiplateforme .NET Core**. Voici comment procéder.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Option 1 : Utiliser la boîte de dialogue Nouveau projet

1. Cliquez sur le lien **Ouvrir Visual Studio Installer** dans le volet gauche de la boîte de dialogue **Nouveau projet**.

   ![Cliquer sur le lien Ouvrir Visual Studio Installer dans la boîte de dialogue Nouveau projet](./media/csharp-open-visual-studio-installer-generic-dark.png)

1. Visual Studio Installer est lancé. Choisissez la charge de travail **Développement multiplateforme .NET Core**, puis choisissez **Modifier**.

   ![Charge de travail Développement multiplateforme .Net Core dans Visual Studio Installer](./media/dot-net-core-xplat-dev-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Option 2 : Utiliser la barre de menus Outils

1. Quittez la boîte de dialogue **Nouveau projet** puis, dans la barre de menus supérieure, choisissez **Outils** > **Obtenir les outils et fonctionnalités**.

1. Visual Studio Installer est lancé. Choisissez la charge de travail **Développement multiplateforme .NET Core**, puis choisissez **Modifier**.

## <a name="create-the-app"></a>Créer l’application

Tout d’abord, nous allons découvrir certaines notions mathématiques de base relatives aux entiers en C#. Nous ajouterons ensuite du code pour créer une calculatrice de base. Ensuite, nous allons modifier le code pour ajouter des fonctionnalités. Après cela, nous allons déboguer l’application pour rechercher et corriger les erreurs. Enfin, nous affinerons le code pour le rendre plus efficace.

Commençons par quelques notions mathématiques relatives aux entiers en C#.

1. Dans l’éditeur de code, supprimez le code « Hello World » par défaut.

    ![Supprimer le code Hello World par défaut de votre nouvelle application de calculatrice](./media/csharp-console-calculator-deletehelloworld.png)

   Plus précisément, supprimez la ligne indiquant `Console.WriteLine("Hello World!");`.

1. À la place, tapez le code suivant :

    ```csharp
            int a = 42;
            int b = 119;
            int c = a + b;
            Console.WriteLine(c);
            Console.ReadKey();
    ```
1. Cliquez sur **Calculator** pour exécuter votre programme, ou appuyez sur **F5**.

   ![Cliquer sur le bouton Calculator pour exécuter l’application à partir de la barre d’outils](./media/csharp-console-calculator-button.png)

   Une fenêtre de console s’ouvre en affichant la somme de 42 + 119.

1. Essayez maintenant de changer la ligne de code `int c = a + b;` en utilisant un autre opérateur, par exemple `-` pour la soustraction, `*` pour la multiplication ou */* pour la division.

    Notez qu’après avoir changé d’opérateur et exécuté le programme, le résultat change également.

Continuons en ajoutant un ensemble plus complexe de code de calculatrice à votre projet.

1. Supprimez tout le code que vous voyez dans l’éditeur de code.

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

1. Appuyez sur **Ctrl** + **F** pour ouvrir le contrôle **Rechercher et remplacer**.

1. Remplacez chaque instance de la variable `int` par `float`.

    ![Animation du contrôle Rechercher et remplacer montrant comment modifier la variable int en float](./media/find-replace-control-animation.gif)

1. Exécutez à nouveau votre application de calculatrice et divisez **42** par **119**.

   Notez que l’application retourne désormais un chiffre décimal au lieu de zéro.

    ![Fenêtre de console montrant l’application Calculator qui retourne maintenant un nombre décimal en tant que résultat](./media/csharp-console-calculator-decimal.png)

Toutefois, l’application ne produit qu’un résultat décimal. Apportons quelques ajustements au code afin que l’application puisse aussi calculer des valeurs décimales.

1. Utilisez le contrôle **Rechercher et remplacer** (**Ctrl** + **F**) pour remplacer chaque instance de la variable `float` en `double`, et chaque instance de la méthode `Convert.ToInt32` en `Convert.ToDouble`.

1. Exécutez votre application de calculatrice et divisez **42,5** par **119,75**.

   Notez que l’application accepte maintenant les valeurs décimales et retourne un chiffre décimal plus long comme résultat.

    ![Fenêtre de console montrant l’application Calculator qui accepte maintenant les nombres décimaux et retourne un nombre décimal plus long en tant que résultat](./media/csharp-console-calculator-usedecimals.png)

    (Nous corrigerons le nombre de décimales dans la section [Réviser le code](#revise-the-code).)

## <a name="debug-the-app"></a>Déboguer l’application

Nous avons amélioré notre application de calculatrice de base, mais elle ne dispose pas encore des filets de sécurité pour gérer les exceptions, telles que les erreurs d’entrée utilisateur.

Par exemple, si vous essayez de diviser un nombre par zéro, ou entrez un caractère alphabétique lorsque l’application attend un caractère numérique (ou vice versa), l’application cesse de fonctionner et retourne une erreur.

Nous allons passer en revue quelques erreurs d’entrée utilisateur courantes, les rechercher dans le débogueur et les corriger dans le code.

>[!TIP]
>Pour plus d’informations sur le débogueur et son fonctionnement, consultez la page [Premier aperçu du débogueur Visual Studio](../../debugger/debugger-feature-tour.md).

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

## <a name="next-steps"></a>Étapes suivantes

Félicitations ! Vous avez terminé ce didacticiel. Pour plus d’informations, passez aux tutoriels suivants.

> [!div class="nextstepaction"]
> [Continuer avec d’autres tutoriels C#](/dotnet/csharp/tutorials/)

## <a name="see-also"></a>Voir aussi

* [Apprendre à déboguer du code C# dans Visual Studio](tutorial-debugger.md)