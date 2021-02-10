---
title: 'Procédure pas à pas : Développement piloté par les tests'
description: Découvrez comment développer une méthode testée en C# à l’aide de Microsoft Test Framework, que vous pouvez facilement adapter à d’autres langages ou infrastructures de test, comme NUnit.
ms.custom: SEO-VS-2020
ms.date: 07/24/2019
ms.topic: conceptual
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 56bfe2b00efc4af71ca562672ad01423778edecd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943729"
---
# <a name="walkthrough-test-driven-development-using-test-explorer"></a>Procédure pas à pas : développement piloté par les tests à l’aide de l’Explorateur de tests

Créez des tests unitaires pour faire en sorte que votre code continue de fonctionner correctement dans le cas de modifications incrémentielles du code. Vous pouvez utiliser plusieurs Infrastructures pour écrire des tests unitaires, y compris ceux développés par des tiers. Certains frameworks de tests sont spécialisés dans les tests pour différents langages ou plateformes. L'explorateur de tests fournit une interface unique pour les tests unitaires dans l'une de ces infrastructures. Pour plus d’informations sur l’**Explorateur de tests**, consultez [Exécuter des tests unitaires avec l’Explorateur de tests](run-unit-tests-with-test-explorer.md) et [Forum aux questions sur l’Explorateur de tests](test-explorer-faq.md).

Cette procédure pas-à-pas montre comment développer une méthode testée en C# avec de l’infrastructure de tests Microsoft (MSTest, Microsoft Test Framework). Vous pouvez facilement l’adapter à d’autres langages ou d’autres infrastructures de tests, comme NUnit. Pour plus d’informations, consultez [Installer des frameworks de tests unitaires de tiers](install-third-party-unit-test-frameworks.md).

## <a name="create-a-test-and-generate-code"></a>Créer un test et générer du code

1. Créez un projet de **bibliothèque de classes (.NET Standard)** C#. Ce projet contiendra le code que nous voulons tester. Nommez le projet **MyMath**.

2. Dans la même solution, ajoutez un nouveau projet **Projet de test MSTest (.NET Core)**. Nommez le projet **MathTests**.

   ![Nouveaux codes et projets de test](../test/media/test-driven-development-ide.png)

3. Écrivez une méthode de test simple qui vérifie le résultat obtenu pour une entrée spécifique. Ajoutez le code suivant à la classe `UnitTest1` :

   ```csharp
   [TestMethod]
   public void BasicRooterTest()
   {
     // Create an instance to test:
     Rooter rooter = new Rooter();
     // Define a test input and output value:
     double expectedResult = 2.0;
     double input = expectedResult * expectedResult;
     // Run the method under test:
     double actualResult = rooter.SquareRoot(input);
     // Verify the result:
     Assert.AreEqual(expectedResult, actualResult, delta: expectedResult / 100);
   }
   ```

4. Générez un type à partir du code de test.

   1. Placez le curseur sur `Rooter` , puis dans le menu ampoule, choisissez générer le **type’Rooter'**  >  **générer un nouveau type**.

      ![Action rapide Générer un nouveau type](media/test-driven-development-generate-new-type.png)

   2. Dans la boîte de dialogue **Générer le type**, définissez **Projet** sur **MyMath**, le projet de bibliothèque de classes, puis choisissez **OK**.

      ![Boîte de dialogue Générer le type dans Visual Studio 2019](media/test-driven-development-generate-type-dialog.png)

5. Générez une méthode à partir du code de test. Placez le curseur sur `SquareRoot` puis, dans le menu Ampoule, choisissez **Générer la méthode « Rooter.SquareRoot »**.

6. Exécutez le test unitaire.

   1. Pour ouvrir l’**Explorateur de tests**, dans le menu **Tester** ,choisissez **Fenêtres** > **Explorateur de tests**.

   2. Dans l’**Explorateur de tests**, choisissez **Exécuter tout** pour réexécuter le test.

   La solution est générée, et les tests s’exécutent et échouent.

7. Sélectionnez le nom du test.

   Les détails du test apparaissent dans le volet **Récapitulatif des détails du test**.

   ![Récapitulatif des détails du test dans l’Explorateur de tests](media/test-driven-development-test-detail-summary.png)

8. Sélectionnez le lien du haut sous **Arborescence des appels de procédure** pour accéder à l’emplacement où le test a échoué.

À ce stade, vous avez créé un test et un stub que vous pouvez modifier afin que le test réussisse.

## <a name="verify-a-code-change"></a>Vérifier une modification du code

1. Dans le fichier *Class1.cs*, améliorez le code de `SquareRoot` :

    ```csharp
    public double SquareRoot(double input)
    {
        return input / 2;
    }
    ```

2. Dans l' **Explorateur de tests**, choisissez **exécuter tout**.

   La solution est générée, et les tests s’exécutent et réussissent.

   ![Explorateur de tests montrant un test réussi.](../test/media/test-driven-development-passed-test.png)

## <a name="extend-the-range-of-inputs"></a>Étendre la plage des entrées

Pour renforcer votre confiance dans le fonctionnement du code dans tous les cas, ajoutez des tests qui essaient un plus grand nombre de valeurs d’entrée.

> [!TIP]
> Évitez de modifier les tests existants qui réussissent. Au lieu de cela, ajoutez de nouveaux tests. Modifiez les tests existants uniquement lorsque les besoins des utilisateurs changent. Cette stratégie permet de garantir que vous ne perdez pas de fonctionnalités existantes quand vous travaillez pour étendre le code.

1. Dans la classe de test, ajoutez le test suivant, qui essaie une plage de valeurs d’entrée :

    ```csharp
    [TestMethod]
    public void RooterValueRange()
    {
        // Create an instance to test.
        Rooter rooter = new Rooter();

        // Try a range of values.
        for (double expected = 1e-8; expected < 1e+8; expected *= 3.2)
        {
            RooterOneValue(rooter, expected);
        }
    }

    private void RooterOneValue(Rooter rooter, double expectedResult)
    {
        double input = expectedResult * expectedResult;
        double actualResult = rooter.SquareRoot(input);
        Assert.AreEqual(expectedResult, actualResult, delta: expectedResult / 1000);
    }
    ```

2. Dans l' **Explorateur de tests**, choisissez **exécuter tout**.

   Le nouveau test échoue (bien que le premier test réussisse encore). Pour rechercher le point de défaillance, sélectionnez le test qui a échoué, puis examinez les détails dans le volet **Récapitulatif des détails du test**.

3. Examinez la méthode de test pour voir ce qui peut être erroné. Modifiez le code de `SquareRoot` comme suit :

    ```csharp
    public double SquareRoot(double input)
    {
      double result = input;
      double previousResult = -input;
      while (Math.Abs(previousResult - result) > result / 1000)
      {
        previousResult = result;
        result = result - (result * result - input) / (2 * result);
      }
      return result;
    }
    ```

4. Dans l' **Explorateur de tests**, choisissez **exécuter tout**.

   Les deux tests ont réussi maintenant.

## <a name="add-tests-for-exceptional-cases"></a>Ajouter des tests pour des cas exceptionnels

1. Ajoutez un nouveau test pour les entrées négatives :

    ```csharp
    [TestMethod]
    public void RooterTestNegativeInputx()
    {
        Rooter rooter = new Rooter();
        try
        {
            rooter.SquareRoot(-10);
        }
        catch (System.ArgumentOutOfRangeException)
        {
            return;
        }
        Assert.Fail();
    }
    ```

2. Dans l' **Explorateur de tests**, choisissez **exécuter tout**.

   La méthode testée s’exécute en boucle et doit être annulée manuellement.

3. Choisissez **Annuler** dans la barre d’outils de l’**Explorateur de tests**.

   Le test cesse de s’exécuter.

4. Corrigez le code de `SquareRoot` en ajoutant l’instruction `if` suivante au début de la méthode :

    ```csharp
    public double SquareRoot(double input)
    {
        if (input <= 0.0)
        {
            throw new ArgumentOutOfRangeException();
        }
        ...
    ```

5. Dans l' **Explorateur de tests**, choisissez **exécuter tout**.

   Tous les tests réussissent.

## <a name="refactor-the-code-under-test"></a>Refactoriser le code testé

Refactorisez le code, mais ne modifiez pas les tests.

> [!TIP]
> La *refactorisation* est une modification destinée à améliorer l’exécution du code ou à en simplifier la compréhension. Elle n'est pas destinée à modifier le comportement du code. Les tests ne sont donc pas modifiés.
>
> Nous vous recommandons de séparer les étapes de refactorisation des étapes qui étendent les fonctionnalités. En ne modifiant pas les tests, vous pouvez être sûr que vous n'avez pas introduit par erreur des bogues lors de la refactorisation.

1. Changez la ligne qui calcule `result` dans la méthode `SquareRoot` comme suit :

    ```csharp
    public double SquareRoot(double input)
    {
        if (input <= 0.0)
        {
            throw new ArgumentOutOfRangeException();
        }

        double result = input;
        double previousResult = -input;
        while (Math.Abs(previousResult - result) > result / 1000)
        {
            previousResult = result;
            result = (result + input / result) / 2;
            //was: result = result - (result * result - input) / (2*result);
        }
        return result;
    }
    ```

2. Choisissez **Exécuter tout** et vérifiez que tous les tests réussissent.

   ![Explorateur de tests indiquant 3 tests réussis.](../test/media/test-driven-development-three-passed-tests.png)
