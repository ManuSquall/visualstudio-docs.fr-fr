---
title: Tests unitaires du code Visual C#
ms.date: 09/27/2019
ms.topic: conceptual
ms.author: mikejo
author: mikejo5000
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 31fbbfaa5d16dd51776f592b89a7846936b3013f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590863"
---
# <a name="unit-test-c-code"></a>Test unitaire du code C#

Cet article décrit une méthode permettant de créer des tests unitaires pour une classe C# dans une application UWP.

La classe **Rooter,** qui est la classe à l’essai, met en œuvre une fonction qui calcule une estimation de la racine carrée d’un nombre donné.

Cet article démontre *le développement axé sur les tests*. Dans cette approche, vous écrivez d’abord un test qui vérifie un comportement spécifique dans le système que vous testez, puis vous écrivez le code qui passe le test.

## <a name="create-the-solution-and-the-unit-test-project"></a>Créer la solution et le projet de test unitaire

1. Dans le menu **Fichier**, choisissez **Nouveau** > **Projet**.

2. Recherchez et sélectionnez le modèle de projet **Application vide (Windows universel)**.

3. Nommez le projet **Maths**.

4. Dans **Solution Explorer**, cliquez à droite sur la solution et choisissez **Ajouter** > nouveau**projet**.

5. Recherchez et sélectionnez le modèle de projet **Application de tests unitaires (Windows universel)**.

6. Nommez le projet de test **RooterTests**.

## <a name="verify-that-the-tests-run-in-test-explorer"></a>Vérifier l'exécution des tests dans l'explorateur de tests

1. Insérez un peu de code de test dans **TestMethod1** dans le fichier *UnitTest.cs* :

   ```csharp
   [TestMethod]
   public void TestMethod1()
   {
       Assert.AreEqual(0, 0);
   }
   ```

   La <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> classe fournit plusieurs méthodes statiques que vous pouvez utiliser pour vérifier les résultats dans les méthodes de test.

::: moniker range="vs-2017"

2. Dans le menu **Test**, choisissez **Exécuter** > **Tous les tests**.

::: moniker-end

::: moniker range=">=vs-2019"

2. Sur le menu **Test,** choisissez **Run All Tests**.

::: moniker-end

   Le projet de test est généré et exécuté. Soyez patient parce que cela peut prendre un peu de temps. La fenêtre **Test Explorer** apparaît, et le test est répertorié dans les **tests passés**. La vitre **sommaire** au bas de la fenêtre fournit des détails supplémentaires sur le test sélectionné.

## <a name="add-the-rooter-class-to-the-maths-project"></a>Ajouter la classe Rooter au projet Maths

1. Dans **Solution Explorer**, cliquez à droite sur le projet **Maths,** puis choisissez **Add** > **Class**.

2. Nommez le fichier de classe *Rooter.cs*.

3. Ajoutez le code suivant à la classe **Rooter** *Rooter.cs* fichier :

   ```csharp
   public Rooter()
   {
   }

   // estimate the square root of a number
   public double SquareRoot(double x)
   {
       return 0.0;
   }
   ```

   La classe **Rooter** déclare un constructeur et la méthode de l’estimateur **SquareRoot.** La méthode **SquareRoot n’est** qu’une implémentation minimale, juste assez pour tester la structure de base de la configuration de test.

4. Ajoutez `public` le mot clé à la déclaration de classe **Rooter,** afin que le code de test puisse y accéder.

   ```csharp
   public class Rooter
   ```

## <a name="add-a-project-reference"></a>Ajouter une référence au projet

1. Ajoutez une référence du projet RooterTests à l’application Maths.

    1. Dans **Solution Explorer**, cliquez à droite sur le projet **RooterTests,** puis choisissez **Add** > **Reference**.

    2. Dans la boîte de dialogue **Ajouter une référence - RooterTests**, développez **Solution**, puis choisissez **Projets**. Sélectionnez le projet **Maths.**

        ![Ajoutez une référence au projet Maths](../test/media/ute_cs_windows_addreference.png)

2. Ajouter `using` une déclaration au fichier *UnitTest.cs* :

    1. Ouvrir *UnitTest.cs*.

    2. Ajoutez le code suivant sous la ligne `using Microsoft.VisualStudio.TestTools.UnitTesting;` :

       ```csharp
       using Maths;
       ```

3. Ajoutez un test qui utilise la fonction **Rooter.** Ajoutez le code suivant à *UnitTest.cs*:

   ```csharp
   [TestMethod]
   public void BasicTest()
   {
       Maths.Rooter rooter = new Rooter();
       double expected = 0.0;
       double actual = rooter.SquareRoot(expected * expected);
       double tolerance = .001;
       Assert.AreEqual(expected, actual, tolerance);
   }
   ```

   Le nouveau test apparaît dans **Test Explorer** dans le nœud Not **Run Tests.**

4. Pour éviter une erreur de « Charge utile contient deux fichiers ou plus avec le même chemin de destination », dans **Solution Explorer**, étendre le nœud **Propriétés** dans le cadre du projet **Maths,** puis supprimer le fichier *Default.rd.xml.*

::: moniker range="vs-2017"

6. Dans **Test Explorer**, choisissez Run **All**.

   La solution se construit et les tests s’exécutent et passent.

   ![BasicTest passé dans Test Explorer](../test/media/ute_cpp_testexplorer_basictest.png)

::: moniker-end

::: moniker range=">=vs-2019"

6. Dans **Test Explorer**, choisissez Run All **Tests**.

   La solution se construit et les tests s’exécutent et passent.

   ![Test de base passé dans Test Explorer](../test/media/vs-2019/test-explorer-uwp-app.png)

::: moniker-end

Vous avez configuré les projets de test et d’application et vérifié que vous pouvez exécuter des tests qui appellent des fonctions dans le projet d’application. Maintenant, vous pouvez commencer à écrire le code et les tests réels.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a>Augmenter itérativement les tests et les faire réussir

1. Ajouter un nouveau test appelé **RangeTest**:

   ```csharp
   [TestMethod]
   public void RangeTest()
   {
       Rooter rooter = new Rooter();
       for (double v = 1e-6; v < 1e6; v = v * 3.2)
       {
           double expected = v;
           double actual = rooter.SquareRoot(v*v);
           double tolerance = expected/1000;
           Assert.AreEqual(expected, actual, tolerance);
       }
   }
   ```

   > [!TIP]
   > Nous vous recommandons de ne pas modifier les tests ayant réussi. Ajoutez un nouveau test à la place.

2. Exécutez le test **RangeTest** et vérifiez qu’il échoue.

   ![RangeTest a échoué](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

   > [!TIP]
   > Immédiatement après avoir écrit un test, exécutez-le pour vérifier qu’il échoue. Vous évitez ainsi de commettre l'erreur d'écrire un test qui n'échoue jamais.

3. Améliorez le code testé afin que le nouveau test réussisse. Modifier la fonction **SquareRoot** en *Rooter.cs* à ceci :

   ```csharp
   public double SquareRoot(double x)
   {
       double estimate = x;
       double diff = x;
       while (diff > estimate / 1000)
       {
           double previousEstimate = estimate;
           estimate = estimate - (estimate * estimate - x) / (2 * estimate);
           diff = Math.Abs(previousEstimate - estimate);
       }
       return estimate;
   }
   ```

::: moniker range="vs-2017"

4. Dans **Test Explorer**, choisissez Run **All**.

::: moniker-end

::: moniker range=">=vs-2019"

4. Dans **Test Explorer**, choisissez Run All **Tests**.

::: moniker-end

   Les trois tests réussissent maintenant.

> [!TIP]
> Développez le code en ajoutant les tests individuellement. Assurez-vous que tous les tests réussissent après chaque itération.

## <a name="refactor-the-code"></a>Refactoriser le code

Dans cette section, vous refactorez à la fois le code d’application et de test, puis réexécutez les tests pour vous assurer qu’ils réussissent toujours.

### <a name="simplify-the-square-root-estimation"></a>Simplifier l’estimation de la racine carrée

1. Simplifier le calcul central de la fonction **SquareRoot** en modifiant une ligne de code, comme suit :

    ```csharp
    // Old code
    //estimate = estimate - (estimate * estimate - x) / (2 * estimate);

    // New code
    estimate = (estimate + x/estimate) / 2.0;
    ```

2. Exécutez tous les tests pour vous assurer que vous n’avez pas introduit une régression. Ils devraient tous passer.

> [!TIP]
> Un ensemble stable de tests unitaires corrects est l'assurance que vous n'avez pas créé de bogues lors de la modification du code.

### <a name="eliminate-duplicated-code"></a>Éliminer le code dupliqué

La méthode **RangeTest** code dur le *tolerance* dénominateur de la <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> variable de tolérance qui est passé à la méthode. Si vous prévoyez d’ajouter des tests supplémentaires qui utilisent le même calcul de tolérance, l’utilisation d’une valeur codée en code dur dans plusieurs emplacements rend le code plus difficile à maintenir.

1. Ajoutez une méthode d’aide privée à la classe **UnitTest1** pour calculer la valeur de tolérance, puis appelez cette méthode de **RangeTest**.

    ```csharp
    private double ToleranceHelper(double expected)
    {
        return expected / 1000;
    }

    ...

    [TestMethod]
    public void RangeTest()
    {
        ...
        // Old code
        // double tolerance = expected/1000;

        // New code
        double tolerance = ToleranceHelper(expected);
    }
    ...
    ```

2. Exécutez **RangeTest** pour s’assurer qu’il passe toujours.

> [!TIP]
> Si vous ajoutez une méthode d’aide à une classe de test, et que vous <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> ne voulez pas qu’elle apparaisse dans Test **Explorer**, n’ajoutez pas l’attribut à la méthode.

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : Développement piloté par test à l’aide de Test Explorer](quick-start-test-driven-development-with-test-explorer.md)
