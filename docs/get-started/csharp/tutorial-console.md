---
title: 'Tutorial: Créer une application simple console C'
description: Découvrez comment créer une application console C# dans Visual Studio, étape par étape.
ms.custom: seodec18, get-started
ms.date: 02/18/2020
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 528887c477814b7011cf941a9198f83701beee54
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "78215436"
---
# <a name="tutorial-create-a-simple-c-console-app-in-visual-studio"></a>Tutorial: Créer une application simple console C dans Visual Studio

Dans ce tutoriel pour C#, vous allez utiliser Visual Studio afin de créer et d’exécuter une application console tout en découvrant certaines fonctionnalités de l’IDE (environnement de développement intégré) Visual Studio.

::: moniker range="vs-2017"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) pour l’installer gratuitement.

::: moniker-end

::: moniker range="vs-2019"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads) pour l’installer gratuitement.

::: moniker-end

## <a name="create-a-project"></a>Création d’un projet

Commençons par créer un projet d’application C#. Le type de projet inclut tous les fichiers de modèle dont vous aurez besoin au départ.

::: moniker range="vs-2017"

1. Ouvrez Visual Studio 2017.

2. De la barre de menu haut, choisissez **File** > **New** > **Project**.
   (Alternativement, appuyez sur **Ctrl**+**Shift**+**N**).

3. Dans le volet gauche de la boîte de dialogue **Nouveau projet**, développez **C#**, puis choisissez **.NET Core**. Dans le volet central, choisissez **Application console (.NET Core)**. Ensuite, nommez le fichier ***Calculator***.

   ![Modèle de projet d’application console (.NET Core) dans la boîte de dialogue Nouveau projet dans l’IDE de Visual Studio](./media/new-project-csharp-calculator-console-app.png)

### <a name="add-a-workload-optional"></a>Ajouter une charge de travail (facultatif)

Si vous ne voyez pas le modèle de projet **Application console (.NET Core)**, vous pouvez l’obtenir en ajoutant la charge de travail **Développement multiplateforme .NET Core**. Voici comment faire.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Option 1 : Utiliser la boîte de dialogue Nouveau projet

1. Cliquez sur le lien **Ouvrir Visual Studio Installer** dans le volet gauche de la boîte de dialogue **Nouveau projet**.

   ![Cliquer sur le lien Ouvrir Visual Studio Installer dans la boîte de dialogue Nouveau projet](./media/csharp-open-visual-studio-installer-generic-dark.png)

1. Visual Studio Installer est lancé. Choisissez la charge de travail **Développement multiplateforme .NET Core**, puis choisissez **Modifier**.

   ![Charge de travail Développement multiplateforme .Net Core dans le programme d’installation de Visual Studio](./media/dot-net-core-xplat-dev-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Option 2 : Utiliser la barre de menus Outils

1. Quittez la boîte de dialogue **Nouveau projet** puis, dans la barre de menus supérieure, choisissez **Outils** > **Obtenir les outils et fonctionnalités**.

1. Visual Studio Installer est lancé. Choisissez la charge de travail **Développement multiplateforme .NET Core**, puis choisissez **Modifier**.

::: moniker-end

::: moniker range="vs-2019"

1. Ouvrez Visual Studio 2019.

1. Sur la fenêtre de départ, choisissez **Créer un nouveau projet**.

   ![Afficher la fenêtre « Créer un projet »](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Dans la fenêtre **Créer un projet**, entrez ou tapez *console* dans la zone de recherche. Ensuite, choisissez **C#** Dans la liste des langages, puis choisissez **Windows** dans la liste des plateformes. 

   Après avoir appliqué les filtres de langage et de plateforme, choisissez le modèle **Application console (.NET Core)**, puis choisissez **Suivant**.

   ![Choisissez le modèle C# pour l’application console (.NET Framework).](./media/vs-2019/csharp-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > Si vous ne voyez pas le modèle **Application console (.NET Core)**, vous pouvez l’installer à partir de la fenêtre **Créer un projet**. Dans le **Vous ne trouvez pas ce que vous cherchez ?**, choisissez le lien **Installer plus d’outils et de fonctionnalités**.
   >
   > ![Le lien « Installer plus d’outils et de fonctionnalités » du message « Vous ne trouvez pas ce que vous cherchez ? » dans la fenêtre « Créer un projet »](../../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Ensuite, dans Visual Studio Installer, choisissez la charge de travail **Développement multiplateforme .NET Core**.
   >
   > ![Charge de travail Développement multiplateforme .Net Core dans le programme d’installation de Visual Studio](./media/dot-net-core-xplat-dev-workload.png)
   >
   > Après cela, choisissez le bouton **Modifier** dans Visual Studio Installer. Vous pouvez être invité à enregistrer votre travail ; le cas échéant, faites-le. Ensuite, choisissez **Continuer** pour installer la charge de travail. Ensuite, revenez à l’étape 2 de cette procédure « [Créer un projet](#create-a-project) ».

1. Dans la fenêtre **Configurer votre nouveau projet**, tapez ou entrez *Calculator* dans la zone **Nom du projet**. Ensuite, choisissez **Créer**.

   ![Dans la fenêtre « Configurer votre nouveau projet », nommez votre projet « Calculator »](./media/vs-2019/csharp-name-your-calculator-project.png)

   Visual Studio ouvre votre nouveau projet, qui inclut le code de « Hello World » par défaut.
   
::: moniker-end

## <a name="create-the-app"></a>Créer l’application

Tout d’abord, nous allons découvrir certaines notions mathématiques de base relatives aux entiers en C#. Nous ajouterons ensuite du code pour créer une calculatrice de base. Après cela, nous allons déboguer l’application pour rechercher et corriger les erreurs. Enfin, nous affinerons le code pour le rendre plus efficace.

### <a name="explore-integer-math"></a>Explorer les mathématiques avec des entiers

Commençons par quelques notions mathématiques de base relatives aux entiers en C#.

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

    Notez que, quand vous procédez ainsi, la fonctionnalité IntelliSense dans Visual Studio vous offre la possibilité de renseigner automatiquement l’entrée.

    > [!NOTE]
    > L’animation suivante n’est pas destinée à dupliquer le code précédent. Il est destiné uniquement à montrer comment fonctionne la fonction autocomplete.

    ![Animation de code mathématique avec des entiers qui illustre la fonctionnalité de saisie semi-automatique IntelliSense dans l’IDE Visual Studio](./media/integer-math-intellisense.gif)

1. Choisissez le bouton **Démarrer** vert à côté **de Calculator** pour construire et exécuter votre programme, ou appuyez sur **F5**.

   ![Cliquer sur le bouton Calculator pour exécuter l’application à partir de la barre d’outils](./media/csharp-console-calculator-button.png)

   Une fenêtre de console s’ouvre en affichant la somme de 42 + 119, c’est-à-dire **161**.

    ![Fenêtre de console affichant les résultats de code mathématique avec des entiers](./media/csharp-console-integer-math.png)

1. **(Facultatif)** Vous pouvez changer d’opérateur pour modifier le résultat. Par exemple, vous pouvez remplacer l’opérateur `+` dans la ligne de code `int c = a + b;` par `-` pour la soustraction, `*` pour la multiplication ou `/` pour la division. Ensuite, quand vous exécutez le programme, le résultat change également.

1. Fermez la fenêtre de console.

### <a name="add-code-to-create-a-calculator"></a>Ajouter du code pour créer une calculatrice

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
                // Declare variables and then initialize to zero.
                int num1 = 0; int num2 = 0;

                // Display title as the C# console calculator app.
                Console.WriteLine("Console Calculator in C#\r");
                Console.WriteLine("------------------------\n");

                // Ask the user to type the first number.
                Console.WriteLine("Type a number, and then press Enter");
                num1 = Convert.ToInt32(Console.ReadLine());

                // Ask the user to type the second number.
                Console.WriteLine("Type another number, and then press Enter");
                num2 = Convert.ToInt32(Console.ReadLine());

                // Ask the user to choose an option.
                Console.WriteLine("Choose an option from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                // Use a switch statement to do the math.
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
                // Wait for the user to respond before closing.
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

### <a name="add-functionality-to-the-calculator"></a>Ajouter des fonctionnalités à la calculatrice

Modifions le code pour ajouter d’autres fonctionnalités.

### <a name="add-decimals"></a>Ajouter des nombres décimaux

Actuellement, l’application Calculator accepte et retourne des nombres entiers. Elle sera cependant plus précise si nous ajoutons le code permettant de traiter des nombres décimaux.

Comme dans la capture d’écran suivante, si vous exécutez l’application et divisez 42 par 119, votre résultat est 0 (zéro), ce qui n’est pas exact.

![Fenêtre de console montrant l’application Calculator qui ne retourne pas un nombre décimal en tant que résultat](./media/csharp-console-calculator-nodecimal.png)

Corrigeons le code afin qu’il gère les nombres décimaux.

1. Appuyez sur **Ctrl** + **F** pour ouvrir le contrôle De la recherche et **du remplacement.**

1. Remplacez chaque instance de la variable `int` par `float`.

   Veillez à activer/désactiver **Respecter la casse** (**Alt**+**C**) et **Mot entier** (**Alt**+**W**) dans le contrôle **Rechercher et remplacer**.

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

Nous avons amélioré notre application de calculatrice de base, mais elle ne dispose pas encore des filets de sécurité nécessaires pour gérer les exceptions, comme les erreurs des entrées utilisateur.

Par exemple, si vous essayez de diviser un nombre par zéro, ou entrez un personnage alpha lorsque l’application s’attend à un personnage numérique (ou vice versa), l’application peut cesser de fonctionner, retourner une erreur ou retourner un résultat nonnumérique inattendu.

Passons à travers quelques erreurs d’entrée utilisateur commune, les localiser dans le débbugger si elles apparaissent là, et les fixer dans le code.

> [!TIP]
> Pour plus d’informations sur le débogueur et son fonctionnement, consultez la page [Premier aperçu du débogueur Visual Studio](../../debugger/debugger-feature-tour.md).

### <a name="fix-the-divide-by-zero-error"></a>Corriger l’erreur de division par zéro

Lorsque vous essayez de diviser un nombre par zéro, l’application console peut geler et ensuite vous montrer ce qui ne va pas dans l’éditeur de code.

   ![L’éditeur de code Visual Studio affiche l’erreur de division par zéro](./media/csharp-console-calculator-dividebyzero-error.png)

> [!NOTE]
> Parfois, l’application ne gèle pas et le débbuggeur ne montrera pas une erreur de division par zéro. Au lieu de cela, l’application pourrait retourner un résultat nonnumérique inattendu, comme un symbole d’infini. Le correctif de code suivant s’applique toujours.

Nous allons modifier le code pour gérer cette erreur.

1. Supprimez le code qui s’affiche directement entre `case "d":` et le commentaire indiquant `// Wait for the user to respond before closing`.

1. Remplacez-le par le code suivant :

   ```csharp
            // Ask the user to enter a non-zero divisor until they do so.
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

Maintenant, quand vous divisez n’importe quel nombre par zéro, l’application vous demande un autre nombre. Encore mieux: Il ne cessera pas de demander jusqu’à ce que vous fournissez un nombre autre que zéro.

   ![L’éditeur de code Visual Studio affiche l’erreur de division par zéro](./media/csharp-console-calculator-dividebyzero.png)

### <a name="fix-the-format-error"></a>Corriger l’erreur de « format »

Si vous entrez un caractère alphabétique lorsque l’application attend un caractère numérique (ou vice versa), l’application de console se bloque. Visual Studio vous montre alors ce qui est incorrect dans l’éditeur de code.

   ![L’éditeur de code Visual Studio affiche une erreur de format](./media/csharp-console-calculator-format-error.png)

Pour corriger cette erreur, nous devons refactoriser le code que nous avons précédemment entré.

#### <a name="revise-the-code"></a>Réviser le code

Plutôt que de nous appuyer sur la classe `program` pour gérer tout le code, nous allons diviser notre application de deux classes : `Calculator` et `Program`.

La classe `Calculator` gérera le gros du travail de calcul et la classe `Program` gèrera l’interface utilisateur et le travail de capture d’erreur.

Nous pouvons commencer.

1. Supprimer tout `Calculator` dans l’espace nom entre ses accolades d’ouverture et de fermeture :

    ```csharp
    using System;

    namespace Calculator
    {
        
    }
    ```

1. Ensuite, ajoutez une nouvelle classe `Calculator`, comme suit :

    ```csharp
    class Calculator
    {
        public static double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

            // Use a switch statement to do the math.
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
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            return result;
        }
    }

    ```

1. Puis, ajoutez une nouvelle classe `Program`, comme suit :

    ```csharp
    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app.
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            while (!endApp)
            {
                // Declare variables and set to empty.
                string numInput1 = "";
                string numInput2 = "";
                double result = 0;

                // Ask the user to type the first number.
                Console.Write("Type a number, and then press Enter: ");
                numInput1 = Console.ReadLine();

                double cleanNum1 = 0;
                while (!double.TryParse(numInput1, out cleanNum1))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput1 = Console.ReadLine();
                }

                // Ask the user to type the second number.
                Console.Write("Type another number, and then press Enter: ");
                numInput2 = Console.ReadLine();

                double cleanNum2 = 0;
                while (!double.TryParse(numInput2, out cleanNum2))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput2 = Console.ReadLine();
                }

                // Ask the user to choose an operator.
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

                // Wait for the user to respond before closing.
                Console.Write("Press 'n' and Enter to close the app, or press any other key and Enter to continue: ");
                if (Console.ReadLine() == "n") endApp = true;

                Console.WriteLine("\n"); // Friendly linespacing.
            }
            return;
        }
    }
    ```

1. Cliquez sur **Calculator** pour exécuter votre programme, ou appuyez sur **F5**.

1. Suivez les invites et divisez le nombre **42** par le nombre **119**. Votre application doit ressembler à la capture d’écran suivante :

    ![Fenêtre de console montrant l’application Calculator refactorisée qui comprend des invites sur les actions à entreprendre et la gestion des erreurs pour les entrées incorrectes](./media/csharp-console-calculator-refactored.png)

    Notez que vous avez la possibilité d’entrer plus d’équations jusqu'à ce que vous choisissiez de fermer l’application de console. Et nous avons également réduit le nombre de décimales dans le résultat.

## <a name="close-the-app"></a>Fermer l’application

1. Si ce n’est déjà fait, fermez l’application de calculatrice.

1. Fermez la vitre **de sortie** dans Visual Studio.

   ![Fermer le volet Sortie dans Visual Studio](./media/csharp-calculator-close-output-pane.png)

1. Dans Visual Studio, appuyez sur **Ctrl**+**S** pour enregistrer votre application.

1. Fermez Visual Studio.

## <a name="code-complete"></a>Code terminé

Durant ce tutoriel, nous avons apporté de nombreux changements à l’application de calculatrice. L’application gère désormais plus efficacement les ressources de calcul, ainsi que la plupart des erreurs d’entrée utilisateur.

Voici le code complet, au même endroit :

```csharp

using System;

namespace Calculator
{
    class Calculator
    {
        public static double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

            // Use a switch statement to do the math.
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
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                    }
                    break;
                // Return text for an incorrect option entry.
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
            // Display title as the C# console calculator app.
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            while (!endApp)
            {
                // Declare variables and set to empty.
                string numInput1 = "";
                string numInput2 = "";
                double result = 0;

                // Ask the user to type the first number.
                Console.Write("Type a number, and then press Enter: ");
                numInput1 = Console.ReadLine();

                double cleanNum1 = 0;
                while (!double.TryParse(numInput1, out cleanNum1))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput1 = Console.ReadLine();
                }

                // Ask the user to type the second number.
                Console.Write("Type another number, and then press Enter: ");
                numInput2 = Console.ReadLine();

                double cleanNum2 = 0;
                while (!double.TryParse(numInput2, out cleanNum2))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput2 = Console.ReadLine();
                }

                // Ask the user to choose an operator.
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

                // Wait for the user to respond before closing.
                Console.Write("Press 'n' and Enter to close the app, or press any other key and Enter to continue: ");
                if (Console.ReadLine() == "n") endApp = true;

                Console.WriteLine("\n"); // Friendly linespacing.
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

* [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
* [Apprendre à déboguer du code C# dans Visual Studio](tutorial-debugger.md)
