---
title: Bien démarrer avec des applications console C# dans Visual Studio
description: Découvrez comment créer une application console C# dans Visual Studio, étape par étape.
ms.custom: ''
ms.date: 10/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: tutorial
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 3450572e4cf4959530599c5eea9efb3168485b58
ms.sourcegitcommit: 401be39a42ffe007593528b5bba62583ca9fcafd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2018
ms.locfileid: "50244370"
---
# <a name="tutorial-get-started-with-a-c-console-app-in-visual-studio"></a>Tutoriel : Bien démarrer avec une application console C# dans Visual Studio

Dans ce tutoriel pour C# vous allez utiliser Visual Studio afin de créer et d’exécuter une application console tout en explorant certaines fonctionnalités de [l’environnement de développement intégré (IDE) Visual Studio](visual-studio-ide.md).

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) pour l’installer gratuitement.

## <a name="create-a-project"></a>Créer un projet

Commençons par créer un projet d’application C#. Le type de projet inclut tous les fichiers de modèle dont vous aurez besoin au départ.

1. Ouvrez Visual Studio 2017.

2. Dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet**.

3. Dans le volet gauche de la boîte de dialogue **Nouveau projet**, développez **C#**, puis choisissez **.NET Core**. Dans le volet central, choisissez **Application console (.NET Core)**. Ensuite, nommez le fichier *Calculator*.

   ![Modèle de projet d’application console (.NET Core) dans la boîte de dialogue Nouveau projet dans l’IDE de Visual Studio](../ide/media/new-project-csharp-calculator-console-app.png)

### <a name="add-a-workgroup-optional"></a>Ajouter un groupe de travail (facultatif)

Si vous ne voyez pas le modèle de projet **Application console (.NET Core)**, vous pouvez l’obtenir en ajoutant la charge de travail **Développement multiplateforme .NET Core**. Vous pouvez ajouter cette charge de travail de l’une des deux manières suivantes, en fonction des mises à jour de Visual Studio 2017 qui sont installées sur votre ordinateur.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Option 1 : Utiliser la boîte de dialogue Nouveau projet

1. Cliquez sur le lien **Ouvrir Visual Studio Installer** dans le volet gauche de la boîte de dialogue **Nouveau projet**.

   ![Cliquer sur le lien Ouvrir Visual Studio Installer dans la boîte de dialogue Nouveau projet](../ide/media/csharp-open-visual-studio-installer-generic-dark.png)

1. Visual Studio Installer est lancé. Choisissez la charge de travail **Développement multiplateforme .NET Core**, puis choisissez **Modifier**.

   ![Charge de travail Développement multiplateforme .Net Core dans Visual Studio Installer](../ide/media/dot-net-core-xplat-dev-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Option 2 : Utiliser la barre de menus Outils

1. Quittez la boîte de dialogue **Nouveau projet** puis, dans la barre de menus supérieure, choisissez **Outils** > **Obtenir les outils et fonctionnalités**.

1. Visual Studio Installer est lancé. Choisissez la charge de travail **Développement multiplateforme .NET Core**, puis choisissez **Modifier**.

## <a name="create-a-c-console-calculator-app"></a>Créer une application « C# Console Calculator »

1. Après avoir créé **l’application console C#**, entrez ou collez le code suivant dans l’éditeur de code :

    ```csharp
    using System;

    namespace Calculator
    {
        class Program
        {
            static void Main(string[] args)
            {
                // Declare variables and then instantiate to zero
                double num1 = 0; double num2 = 0;

                // Display title as the C# console calculator app
                Console.WriteLine("Console Calculator in C#\r");
                Console.WriteLine("------------------------\n");

                // Ask the user to type the first number
                Console.WriteLine("Type a number, and then press Enter");
                num1 = Convert.ToDouble(Console.ReadLine());

                // Ask the user to type the second number
                Console.WriteLine("Type another number, and then press Enter");
                num2 = Convert.ToDouble(Console.ReadLine());

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
                        // Ask the user to enter a non-zero divisor until they do so
                        while (num2 == 0)
                        {
                            Console.WriteLine("Enter a non-zero divisor: ");
                            num2 = Convert.ToDouble(Console.ReadLine());
                        }
                        Console.WriteLine($"Your result: {num1} / {num2} = " + (num1 / num2));
                        break;
                    // Return text for an incorrect option entry
                    default:
                        Console.WriteLine("That is an incorrect option entry, please try again.");
                        break;
                }
                // Wait for the user to respond before closing
                Console.Write("Press any key to close the Calculator console app...");
                Console.ReadKey();
            }
        }
    }
    ```

   Le code qui apparaît après `static void Main(string[] args)` devrait ressembler à la capture d’écran suivante :

   ![Éditeur de code montrant C# Console Calculator](../ide/media/csharp-console-calculator-code.png)

1. Cliquez sur **Calculator** pour exécuter votre programme, ou appuyez sur **F5**.

   ![Cliquer sur le bouton Calculator pour exécuter l’application à partir de la barre d’outils](../ide/media/csharp-console-calculator-button.png)

1. Votre application s’affiche dans la fenêtre de console. Une fois que vous avez suivi les invites, votre application devrait ressembler à la capture d’écran suivante :

    ![Fenêtre de console montrant l’application Calculator, avec des invites sur les actions à effectuer.](../ide/media/csharp-console-calculator.png)

### <a name="close-the-app"></a>Fermer l’application

1. Appuyez sur n’importe quelle touche pour fermer l’application Calculator.

1. Fermez le volet **Sortie** dans Visual Studio.

   ![Fermer le volet Sortie dans Visual Studio](../ide/media/csharp-calculator-close-output-pane.png)

1. Fermez Visual Studio.

## <a name="quick-answers-faq"></a>Questions fréquentes (FAQ) et réponses rapides

Voici des Questions fréquentes (FAQ) rapides pour mettre en lumière certains concepts clés.

### <a name="what-is-c"></a>Qu’est-ce que C# ?

C# est un langage de programmation de type sécurisé qui s’exécute sur .NET Framework et .NET Core. Avec C#, vous pouvez créer des applications Windows, des applications client-serveur, des applications de base de données, des services web XML, des composants distribués et bien plus encore.

### <a name="what-is-visual-studio"></a>Qu’est-ce que Visual Studio ?

Visual Studio est une suite de développement intégrée d’outils de productivité pour les développeurs. Il s’agit d’un programme qui sert à créer des applications et des programmes.

### <a name="what-is-a-console-app"></a>Qu’est-ce qu’une application console ?

Une application console prend une entrée et affiche la sortie dans une fenêtre de ligne de commande, également appelée console.

### <a name="what-is-net-core"></a>Qu'est-ce que le .NET Core ?

.NET Core est la suite logique du .NET Framework. Là où le .NET Framework vous permettait de partager du code entre les langages de programmation, .NET Core ajoute la capacité à partager du code entre des plateformes. De plus, il est open source.

(.NET Framework et .NET Core comportent des bibliothèques de fonctionnalités prégénérées, ainsi qu’un common language runtime (CLR) qui fonctionne comme une machine virtuelle sur laquelle votre code s’exécute.)

## <a name="next-steps"></a>Étapes suivantes

Félicitations ! Vous avez terminé ce didacticiel. Pour plus d’informations, passez aux tutoriels suivants.

> [!div class="nextstepaction"]
> [Tutoriels C#](/dotnet/csharp/tutorials/)

## <a name="see-also"></a>Voir aussi

* [Cours vidéo Concepts de base de C# pour les débutants](https://mva.microsoft.com/en-us/training-courses/c-fundamentals-for-absolute-beginners-16169)
