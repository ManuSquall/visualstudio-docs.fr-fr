---
title: 'Didacticiel : étendre une application console C# simple'
description: découvrez comment développer une application console C# dans Visual Studio, pas à pas.
ms.custom: vs-acquisition, get-started
ms.date: 04/15/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: j-martens
ms.author: jmartens
manager: jmartens
monikerRange: '>=vs-2019'
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 84a79015dc4b1147f078b0a970df52c553189c92
ms.sourcegitcommit: 4e09130bcd55bb9cb8ad157507c23b67aa209fad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2021
ms.locfileid: "113549496"
---
# <a name="tutorial-extend-a-simple-c-console-app"></a>Didacticiel : étendre une application console C# simple

dans ce didacticiel, vous allez apprendre à utiliser Visual Studio pour étendre l’application console que vous avez créée dans la première partie. vous découvrirez certaines des fonctionnalités de Visual Studio dont vous aurez besoin pour le développement quotidien, telles que la gestion de plusieurs projets et le référencement de packages tiers.

Si vous venez de terminer la [première partie](tutorial-console.md) de cette série, vous disposez déjà de l’application console Calculator.  pour ignorer la partie 1, vous pouvez commencer par ouvrir le projet à partir d’un GitHub référentiel. L’application Calculatrice C# se trouve dans le [référentiel vs-Tutorial-Samples](https://github.com/MicrosoftDocs/vs-tutorial-samples). vous pouvez donc simplement suivre les étapes du [Didacticiel : ouvrir un projet à partir d’un référentiel](../tutorial-open-project-from-repo.md) pour commencer.

## <a name="add-a-new-project"></a>Ajouter un nouveau projet

Le code réel implique de nombreux projets qui fonctionnent ensemble dans une solution. À présent, nous allons ajouter un autre projet à l’application Calculatrice. Il s’agit d’une bibliothèque de classes qui fournit certaines fonctions de calculatrice.

1. dans Visual Studio, vous pouvez utiliser le **fichier** de commandes de menu de niveau supérieur  >  **ajouter**  >  un **nouveau Project** pour ajouter un nouveau projet, mais vous pouvez également cliquer avec le bouton droit sur le nom de projet existant (appelé « nœud de projet ») et ouvrir le menu contextuel du projet (ou menu contextuel). Ce menu contextuel contient de nombreuses façons d’ajouter des fonctionnalités à vos projets. cliquez avec le bouton droit sur le nœud de votre projet dans **Explorateur de solutions**, puis choisissez **ajouter**  >  **un nouveau Project**.

1. Choisissez la bibliothèque de classes de modèles de projet C# **(.NET standard)**.

   ![Capture d’écran de la sélection du modèle de projet de bibliothèque de classes](media/vs-2019/calculator2-add-project-dark.png)

1. Tapez le nom du projet **CalculatorLibrary**, puis choisissez **créer**. Là encore, choisissez .NET 3,1 quand vous y êtes invité. Visual Studio crée le nouveau projet et l’ajoute à la solution.

   ![Capture d’écran de Explorateur de solutions avec le projet de bibliothèque de classes CalculatorLibrary ajouté](media/vs-2019/calculator2-solution-explorer-with-class-library-dark2.png)

1. Au lieu d’avoir *Class1. cs*, renommez le fichier **CalculatorLibrary. cs**. Vous pouvez cliquer sur le nom dans **Explorateur de solutions** pour le renommer, ou cliquer avec le bouton droit et choisir **Renommer**, ou appuyer sur la touche **F2** .

   Vous pouvez être invité à indiquer si vous souhaitez renommer toutes les références à `Class1` dans le fichier. Peu importe la façon dont vous répondez, puisque vous allez remplacer le code dans une étape ultérieure.

1. Nous devons maintenant ajouter une référence de projet, de sorte que le premier projet puisse utiliser des API exposées par la nouvelle bibliothèque de classes.  cliquez avec le bouton droit sur le nœud **dépendances** dans le premier projet, puis choisissez **ajouter une référence de Project**.

   ![capture d’écran de l’élément de menu ajouter Project référence](media/vs-2019/calculator2-add-project-reference-dark.png)

   La boîte de dialogue **Gestionnaire de références** s’affiche. Cette boîte de dialogue vous permet d’ajouter des références à d’autres projets, ainsi que des assemblys et des DLL COM dont vos projets ont besoin.

   ![Capture d’écran de la boîte de dialogue Gestionnaire de références](media/vs-2019/calculator2-ref-manager-dark.png)

1. Dans la boîte de dialogue **Gestionnaire de références** , cochez la case du projet **CalculatorLibrary** , puis choisissez **OK**.  La référence de projet apparaît sous un nœud **projets** dans **Explorateur de solutions**.

   ![Capture d’écran de Explorateur de solutions avec la référence de projet](media/vs-2019/calculator2-solution-explorer-with-project-reference-dark2.png)

1. Dans *Program. cs*, sélectionnez la `Calculator` classe et tout son code, puis appuyez sur **CTRL + X** pour la couper de Program. cs. Ensuite, dans **CalculatorLibrary**, dans *CalculatorLibrary. cs*, collez le code dans l’espace de `CalculatorLibrary` noms. Ensuite, faites de la classe Calculator `public` pour l’exposer en dehors de la bibliothèque. Le code dans *CalculatorLibrary. cs* doit maintenant ressembler au code suivant :

   ```csharp
   using System;

    namespace CalculatorLibrary
    {
        public class Calculator
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
    }
   ```

1. Le premier projet a une référence, mais vous verrez une erreur indiquant que l’appel Calculator. nooperation ne se résout pas. Étant donné que CalculatorLibrary se trouve dans un espace de noms différent, ajoutez l' `CalculatorLibrary` espace de noms pour une référence qualifiée complète.

   ```csharp
   result = CalculatorLibrary.Calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   Essayez d’ajouter une directive using au début du fichier à la place :

   ```csharp
   using CalculatorLibrary;
   ```

   Cette modification devrait vous permettre de supprimer l’espace de noms CalculatorLibrary du site d’appel, mais il y a maintenant une ambiguïté. La classe est-elle `Calculator` dans CalculatorLibrary, ou est-ce que l’espace de noms ?  Pour résoudre l’ambiguïté, renommez l’espace de noms `CalculatorProgram` .

   ```csharp
   namespace CalculatorProgram
   ```

## <a name="reference-net-libraries-write-to-a-log"></a>Référencer des bibliothèques .NET : écrire dans un journal

1. Supposons que vous souhaitez maintenant ajouter un journal de toutes les opérations et l’écrire dans un fichier texte. La `Trace` classe .NET fournit cette fonctionnalité. (C’est également utile pour les techniques de débogage d’impression de base.)  La classe trace se trouve dans System. Diagnostics, et nous aurons besoin de classes System.IO comme `StreamWriter` , commencez par ajouter les directives using en haut de *CalculatorLibrary. cs*:

   ```csharp
   using System.IO;
   using System.Diagnostics;
   ```

1. En examinant la façon dont la classe trace est utilisée, vous devez conserver une référence pour la classe, qui est associée à un FileStream. Cela signifie que la calculatrice fonctionne mieux comme un objet. nous allons donc ajouter un constructeur au début de la classe Calculator dans *CalculatorLibrary. cs*.

   ```csharp
   public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculator.log");
            Trace.Listeners.Add(new TextWriterTraceListener(logFile));
            Trace.AutoFlush = true;
            Trace.WriteLine("Starting Calculator Log");
            Trace.WriteLine(String.Format("Started {0}", System.DateTime.Now.ToString()));
        }

    public double DoOperation(double num1, double num2, string op)
        {
   ```

1. Et que nous devons modifier la `DoOperation` méthode statique en une méthode membre, supprimez le `static` mot clé.  Nous allons également ajouter la sortie à chaque calcul pour le journal, de sorte que l’opération de l’action ressemble au code suivant :

   ```csharp
   public double DoOperation(double num1, double num2, string op)
   {
        double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

        // Use a switch statement to do the math.
        switch (op)
        {
            case "a":
                result = num1 + num2;
                Trace.WriteLine(String.Format("{0} + {1} = {2}", num1, num2, result));
                break;
            case "s":
                result = num1 - num2;
                Trace.WriteLine(String.Format("{0} - {1} = {2}", num1, num2, result));
                break;
            case "m":
                result = num1 * num2;
                Trace.WriteLine(String.Format("{0} * {1} = {2}", num1, num2, result));
                break;
            case "d":
                // Ask the user to enter a non-zero divisor.
                if (num2 != 0)
                {
                    result = num1 / num2;
                    Trace.WriteLine(String.Format("{0} / {1} = {2}", num1, num2, result));
                }
                    break;
            // Return text for an incorrect option entry.
            default:
                break;
        }
        return result;
    }
   ```

1. À présent, dans *Program. cs*, l’appel statique est marqué d’un trait ondulé rouge. Pour résoudre ce problème, créez une `calculator` variable en ajoutant la ligne suivante juste avant la `while (!endApp)` boucle :

   ```csharp
   Calculator calculator = new Calculator();
   ```

   Et modifier le site d’appel pour `DoOperation` comme suit, afin que cela fasse référence à l’objet nommé `calculator` en minuscules, ce qui en fait un appel de membre, plutôt qu’un appel à une méthode statique :

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

1. Réexécutez le programme, puis, lorsque vous avez terminé, cliquez avec le bouton droit sur le nœud du projet et choisissez **ouvrir le dossier dans l’Explorateur de fichiers**, puis accédez au dossier de sortie dans l’Explorateur de fichiers. Il peut s’agir de *bin/debug/netcoreapp 3.1* et ouvrir le fichier *Calculator. log* .

    ```output
    Starting Calculator Log
    Started 7/9/2020 1:58:19 PM
    1 + 2 = 3
    3 * 3 = 9
    ```

À ce stade, *CalculatorLibrary. cs* doit ressembler à ceci :

```csharp
using System;
using System.IO;
using System.Diagnostics;


namespace CalculatorLibrary
{
    public class Calculator
    {

        public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculator.log");
            Trace.Listeners.Add(new TextWriterTraceListener(logFile));
            Trace.AutoFlush = true;
            Trace.WriteLine("Starting Calculator Log");
            Trace.WriteLine(String.Format("Started {0}", System.DateTime.Now.ToString()));
        }

        public double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    Trace.WriteLine(String.Format("{0} + {1} = {2}", num1, num2, result));
                    break;
                case "s":
                    result = num1 - num2;
                    Trace.WriteLine(String.Format("{0} - {1} = {2}", num1, num2, result));
                    break;
                case "m":
                    result = num1 * num2;
                    Trace.WriteLine(String.Format("{0} * {1} = {2}", num1, num2, result));
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                        Trace.WriteLine(String.Format("{0} / {1} = {2}", num1, num2, result));
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            return result;
        }
    }
}
```

Et *Program. cs* doivent ressembler à ce qui suit :

```csharp
using System;
using CalculatorLibrary;

namespace CalculatorProgram
{
   
    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app.
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            Calculator calculator = new Calculator();
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
                    result = calculator.DoOperation(cleanNum1, cleanNum2, op); 
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

## <a name="add-a-nuget-package-write-to-a-json-file"></a>ajouter un Package de NuGet : écrire dans un fichier JSON

1. Supposons à présent que nous souhaitons générer les opérations au format JSON, un format très répandu et portable pour le stockage des données d’objet. pour implémenter cette fonctionnalité, nous devons référencer le package NuGet Newtonsoft.Js. les packages de NuGet constituent le vecteur principal de distribution des bibliothèques de classes .net. dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **dépendances** pour le projet CalculatorLibrary, puis choisissez **gérer les Packages de NuGet**.

   ![capture d’écran de la gestion des Packages de NuGet dans le menu contextuel](media/vs-2019/calculator2-manage-nuget-packages-dark2.png)

   le Gestionnaire de package NuGet s’ouvre.

   ![Capture d’écran du Gestionnaire de package NuGet](media/vs-2019/calculator2-nuget-package-manager-dark.png)

1. Recherchez Newtonsoft.Jssur le package, puis choisissez **installer**.

   ![capture d’écran de Newtonsoft NuGet informations sur le package](media/vs-2019/calculator2-nuget-newtonsoft-json-dark2.png)

   Le package est téléchargé et ajouté à votre projet et une nouvelle entrée s’affiche dans le nœud Références de **Explorateur de solutions**.

1. Ajoutez une directive using pour System.IO et Newtonsoft.Jssur le package au début de *CalculatorLibrary. cs*.

   ```csharp
   using Newtonsoft.Json;
   ```

1. À présent, remplacez le constructeur de Calculator par le code suivant et créez l’objet membre JsonWriter :

   ```csharp
        JsonWriter writer;

        public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculatorlog.json");
            logFile.AutoFlush = true;
            writer = new JsonTextWriter(logFile);
            writer.Formatting = Formatting.Indented;
            writer.WriteStartObject();
            writer.WritePropertyName("Operations");
            writer.WriteStartArray();
        }
   ```

1. Modifiez la `DoOperation` méthode pour ajouter le code du writer JSON :

   ```csharp
        public double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.
            writer.WriteStartObject();
            writer.WritePropertyName("Operand1");
            writer.WriteValue(num1);
            writer.WritePropertyName("Operand2");
            writer.WriteValue(num2);
            writer.WritePropertyName("Operation");
            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    writer.WriteValue("Add");
                    break;
                case "s":
                    result = num1 - num2;
                    writer.WriteValue("Subtract");
                    break;
                case "m":
                    result = num1 * num2;
                    writer.WriteValue("Multiply");
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                        writer.WriteValue("Divide");
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            writer.WritePropertyName("Result");
            writer.WriteValue(result);
            writer.WriteEndObject();

            return result;
        }
   ```

1. Vous devez ajouter une méthode pour terminer la syntaxe JSON une fois que l’utilisateur a terminé d’entrer les données d’opération.

   ```csharp
    public void Finish()
    {
        writer.WriteEndArray();
        writer.WriteEndObject();
        writer.Close();
    }
   ```

1. Et dans *Program. cs*, ajoutez un appel pour terminer à la fin.

   ```csharp
            // And call to close the JSON writer before return
            calculator.Finish();
            return;
        }
   ```

1. Générez et exécutez l’application, et une fois que vous avez terminé d’entrer quelques opérations, fermez l’application correctement à l’aide de la commande « n ».  À présent, ouvrez le fichier calculatorlog.jssur et vous devriez voir un résultat semblable à ce qui suit :

   ```json
   {
    "Operations": [
        {
        "Operand1": 2.0,
        "Operand2": 3.0,
        "Operation": "Add",
        "Result": 5.0
        },
        {
        "Operand1": 3.0,
        "Operand2": 4.0,
        "Operation": "Multiply",
        "Result": 12.0
        }
    ]
   }
   ```

## <a name="debug-set-and-hit-a-breakpoint"></a>Débogage : définir et atteindre un point d’arrêt

le débogueur Visual Studio est un outil puissant qui vous permet d’exécuter votre code pas à pas, afin de trouver le point exact où vous avez fait une erreur de programmation. Vous comprenez ensuite les corrections que vous devez apporter dans votre code. Visual Studio vous permet d’effectuer des modifications temporaires pour pouvoir continuer à exécuter le programme.

1. Dans *Program. cs*, cliquez sur la marge à gauche du code suivant (ou ouvrez le menu contextuel et choisissez **point d’arrêt**  >  **Insérer un point d’arrêt** ou appuyez sur **F9**) :

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   Le cercle rouge qui s’affiche indique un point d’arrêt. Vous pouvez utiliser des points d’arrêt pour suspendre votre application et inspecter le code. Vous pouvez définir un point d’arrêt sur n’importe quelle ligne de code exécutable.

   ![Capture d’écran de la définition d’un point d’arrêt](media/vs-2019/calculator-2-debug-set-breakpoint.png)

1. Générez et exécutez l'application.

1. Dans l’application en cours d’exécution, tapez des valeurs pour le calcul :

   - Pour le premier nombre, tapez **8** et entrez-le.
   - Pour le deuxième nombre, tapez **0** et entrez-le.
   - Pour l’opérateur, commençons par le plaisir. tapez **d** et entrez-le.

   L’application s’interrompt là où vous avez créé le point d’arrêt, ce qui est indiqué par le pointeur jaune à gauche et le code en surbrillance. Le code en surbrillance n’a pas encore été exécuté.

   ![Capture d’écran de l’atteinte d’un point d’arrêt](media/vs-2019/calculator-2-debug-hit-breakpoint.png)

   Maintenant, une fois l’application suspendue, vous pouvez inspecter l’état de votre application.

## <a name="debug-view-variables"></a>Débogage : afficher les variables

1. Dans le code en surbrillance, pointez sur des variables telles que `cleanNum1` et `op` . Vous voyez les valeurs actuelles de ces variables ( `8` et `d` , respectivement), qui apparaissent dans les DataTips.

   ![Capture d’écran de l’affichage d’un DataTip](media/vs-2019/calculator-2-debug-view-datatip.png)

   Lors du débogage, le fait de vérifier si les variables contiennent les valeurs que vous prévoyez de conserver est souvent essentiel pour résoudre les problèmes.

2. Dans le volet inférieur, examinez la fenêtre **variables locales** . (S’il est fermé, choisissez **Déboguer**  >  **Windows**  >  **Locales** pour l’ouvrir.)

   Dans la fenêtre variables locales, vous voyez chaque variable qui est actuellement dans la portée, ainsi que sa valeur et son type.

   ![Capture d’écran de la fenêtre variables locales](media/vs-2019/calculator-2-debug-locals-window.png)

3. Examinez la fenêtre **automatique** .

   La fenêtre automatique est semblable à la fenêtre **variables locales** , mais elle affiche les variables qui précèdent et suivent la ligne de code en cours où votre application est suspendue.

   Ensuite, vous allez exécuter le code dans le débogueur une instruction à la fois, qui est appelée *pas à pas*.

## <a name="debug-step-through-code"></a>Débogage : pas à pas détaillé dans le code

1. Appuyez sur **F11** (ou **déboguez**  >  **pas à pas** détaillé).

   À l’aide de la commande pas à pas détaillé, l’application exécute l’instruction en cours et avance à l’instruction exécutable suivante (généralement la ligne de code suivante). Le pointeur jaune sur la gauche indique toujours l’instruction en cours.

   ![Capture d’écran de la commande pas à pas détaillé](media/vs-2019/calculator-2-debug-step-into.png)

   Vous venez d’examiner la `DoOperation` méthode dans la `Calculator` classe.

1. Pour obtenir un aperçu hiérarchique du déroulement de votre programme, examinez la fenêtre **pile des appels** . (S’il est fermé, choisissez **Déboguer**  >  **Windows**  >  **Pile des appels**.)

   ![Capture d’écran de la pile des appels](media/vs-2019/calculator-2-debug-call-stack.png)

   Cette vue affiche la `Calculator.DoOperation` méthode actuelle, indiquée par le pointeur jaune, et la deuxième ligne affiche la fonction qui l’a appelée, à partir de la `Main` méthode dans *Program. cs*. La fenêtre **Pile des appels** montre l’ordre dans lequel les méthodes et les fonctions sont appelées. En outre, il permet d’accéder à de nombreuses fonctionnalités du débogueur, telles que **accéder au code source**, à partir du menu contextuel.

1. Appuyez sur **F10** (ou **déboguez**  >  **pas à pas**) plusieurs fois jusqu’à ce que l’application s’arrête sur l' `switch` instruction.

   ```csharp
   switch (op)
   {
   ```

   La commande pas à pas principal est similaire à la commande pas à pas détaillé, sauf que si l’instruction en cours appelle une fonction, le débogueur exécute le code dans la fonction appelée et n’interrompt pas l’exécution tant que la fonction n’est pas retournée. Le pas à pas principal est un moyen plus rapide de parcourir le code si vous n’êtes pas intéressé par une fonction particulière.

1. Appuyez sur **F10** une fois de plus pour que l’application s’arrête sur la ligne de code suivante.

   ```csharp
   if (num2 != 0)
   {
   ```

   Ce code recherche un cas de division par zéro. Si l’application continue, elle lèvera une exception générale (une erreur), mais supposons que vous considériez ce bogue comme un bogue et que vous souhaitez effectuer une autre opération, par exemple afficher la valeur renvoyée réelle dans la console. Une option consiste à utiliser une fonctionnalité du débogueur appelée Edit-and-continue pour apporter des modifications au code, puis à continuer le débogage. Toutefois, nous vous présenterons une astuce différente pour modifier temporairement le workflow d’exécution.

## <a name="debug-test-a-temporary-change"></a>Débogage : tester une modification temporaire

1. Sélectionnez le pointeur jaune, actuellement suspendu sur l' `if (num2 != 0)` instruction, puis faites-le glisser vers l’instruction suivante.

   ```csharp
   result = num1 / num2;
   ```

   En procédant ainsi, l’application ignore complètement l' `if` instruction, ce qui vous permet de voir ce qui se passe lorsque vous divisez par zéro.

1. Appuyez sur **F10** pour exécuter la ligne de code.

1. Pointez sur la `result` variable et vous voyez qu’elle stocke la valeur `Infinity` .

   En C#, `Infinity` est le résultat obtenu lorsque vous divisez par zéro.

1. Appuyez sur **F5** (ou, **Déboguer**  >  **continuer le débogage**).

   Le symbole infini apparaît dans la console à la suite de l’opération mathématique.

1. Fermez l’application correctement à l’aide de la commande’n'.

## <a name="code-complete"></a>Code terminé

Voici le code complet du fichier *CalculatorLibrary. cs* , une fois toutes les étapes terminées :

```csharp
using System;
using System.IO;
using System.Diagnostics;
using Newtonsoft.Json;

namespace CalculatorLibrary
{
    public class Calculator
    {

        JsonWriter writer;

        public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculatorlog.json");
            logFile.AutoFlush = true;
            writer = new JsonTextWriter(logFile);
            writer.Formatting = Formatting.Indented;
            writer.WriteStartObject();
            writer.WritePropertyName("Operations");
            writer.WriteStartArray();
        }

        public double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.
            writer.WriteStartObject();
            writer.WritePropertyName("Operand1");
            writer.WriteValue(num1);
            writer.WritePropertyName("Operand2");
            writer.WriteValue(num2);
            writer.WritePropertyName("Operation");
            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    writer.WriteValue("Add");
                    break;
                case "s":
                    result = num1 - num2;
                    writer.WriteValue("Subtract");
                    break;
                case "m":
                    result = num1 * num2;
                    writer.WriteValue("Multiply");
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                        writer.WriteValue("Divide");
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            writer.WritePropertyName("Result");
            writer.WriteValue(result);
            writer.WriteEndObject();

            return result;
        }

        public void Finish()
        {
            writer.WriteEndArray();
            writer.WriteEndObject();
            writer.Close();
        }
    }
}
```

Et voici le code pour *Program. cs*: 

```csharp
using System;
using CalculatorLibrary;

namespace CalculatorProgram
{
   
    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app.
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            Calculator calculator = new Calculator();
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
                    result = calculator.DoOperation(cleanNum1, cleanNum2, op); 
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
            calculator.Finish();
            return;
        }
    }
}
```

## <a name="next-steps"></a>Étapes suivantes

Félicitations ! Vous avez terminé ce didacticiel. Pour plus d’informations, passez aux tutoriels suivants.

> [!div class="nextstepaction"]
> [Continuer avec d’autres tutoriels C#](/dotnet/csharp/tutorials/)

> [!div class="nextstepaction"]
> [continuer avec Visual Studio vue d’ensemble de l’IDE](/../visual-studio-ide.md)

## <a name="see-also"></a>Voir aussi

- [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
- [Apprendre à déboguer du code C# dans Visual Studio](tutorial-debugger.md)
