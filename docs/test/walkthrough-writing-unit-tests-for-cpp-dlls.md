---
title: 'Procédure : Écrire des tests unitaires pour des DLL C++'
ms.date: 11/04/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: a596281d156882dffbef6e1c0993f2c91015e960
ms.sourcegitcommit: 159ed9d4f56cdc1dff2fd19d9dffafe77e46cd4e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2018
ms.locfileid: "53740164"
---
# <a name="how-to-write-unit-tests-for-c-dlls"></a>Procédure : Écrire des tests unitaires pour des DLL C++

Cette procédure pas à pas décrit comment développer une DLL C++ native en utilisant la méthodologie des tests en premier. Les étapes de base sont les suivantes :

1.  [Créer un projet de test natif](#create_test_project). Le projet de test se trouve dans la même solution que le projet DLL.

2.  [Créer un projet DLL](#create_dll_project). Cette procédure pas à pas crée une DLL, mais la procédure de test d'une DLL existante est similaire.

3.  [Rendre les fonctions DLL visibles par les tests](#make_functions_visible).

4.  [Augmenter itérativement les tests](#iterate). Nous recommandons un cycle « Rouge-Vert-Refactoriser », dans lequel le développement du code est conduit par les tests.

5.  [Déboguer les tests ayant échoué](#debug). Vous pouvez exécuter les tests en mode débogage.

6.  [Refactoriser tout en maintenant les tests inchangés](#refactor). La refactorisation signifie une amélioration de la structure du code sans modification de son comportement externe. Vous pouvez procéder ainsi pour améliorer les performances, l'extensibilité ou la lisibilité du code. Comme le but n'est pas de changer le comportement, vous ne modifiez pas les tests en même temps que vous effectuez une modification de refactorisation du code. Les tests permettent de vérifier que vous n’introduisez pas de bogues lors de la refactorisation.

7.  [Vérifier la couverture](using-code-coverage-to-determine-how-much-code-is-being-tested.md). Les tests unitaires sont plus utiles lorsqu'ils impliquent une plus grande partie de votre code. Vous pouvez découvrir quelles parties de votre code ont été utilisées par les tests.

8.  [Isoler les unités des ressources externes](using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md). En règle générale, une DLL dépend des autres composants du système que vous développez, tels que les autres DLL, les bases de données ou les sous-systèmes à distance. Il est utile de tester chaque unité isolément de ses dépendances. Les composants externes peuvent ralentir les tests. Pendant le développement, les autres composants peuvent ne pas être achevés.

##  <a name="create_test_project"></a> Créer un projet de test unitaire natif

1.  Dans le menu **Fichier**, choisissez **Nouveau** > **Projet**.

     Dans la boîte de dialogue, développez **Installé** > **Modèles** > **Visual C++** > **Test**.

     Choisissez le modèle **Projet de test unitaire natif** ou un autre framework installé de votre choix. Si vous choisissez un autre modèle, comme Google Test ou Boost.Test, les principes de base sont les mêmes, bien que certains détails diffèrent.

     Dans cette procédure pas à pas, le projet de test se nomme `NativeRooterTest`.

     ![Création d'un projet de test unitaire C++](../test/media/utecpp01.png)

2.  Dans le nouveau projet, inspectez **unittest1.cpp**

     ![Projet de test avec TEST&#95;CLASS et TEST&#95;METHOD](../test/media/utecpp2.png)

     Notez que :

    -   Chaque test est défini à l'aide de `TEST_METHOD(YourTestName){...}`.

         Vous n'avez pas à écrire une signature de fonction classique. La signature est créée par la macro TEST_METHOD. La macro génère une fonction d'instance qui retourne void. Elle génère également une fonction statique qui retourne des informations sur la méthode de test. Ces informations permettent à l'Explorateur de tests de trouver la méthode.

    -   Les méthodes de test sont regroupées en classes à l'aide de `TEST_CLASS(YourClassName){...}`.

         Lorsque les tests sont exécutés, une instance de chaque classe de test est créée. Les méthodes de test sont appelées dans un ordre non défini. Vous pouvez définir des méthodes spéciales qui sont appelées avant et après chaque module, classe ou méthode.

3.  Vérifiez que les tests s'exécutent dans l'Explorateur de tests :

    1.  Insérez le code de test :

        ```cpp
        TEST_METHOD(TestMethod1)
        {
            Assert::AreEqual(1,1);
        }
        ```

         Notez que la classe `Assert` fournit plusieurs méthodes statiques que vous pouvez utiliser pour vérifier les résultats dans les méthodes de test.

    2.  Dans le menu **Test**, choisissez **Exécuter** > **Tous les tests**.

         Le test est généré et s'exécute.

         **L’Explorateur de tests** s’affiche.

         Le test s'affiche sous **Tests réussis**.

         ![Explorateur de tests unitaires avec un test réussi](../test/media/utecpp04.png)

##  <a name="create_dll_project"></a> Créer un projet DLL

1.  Créez un projet **Visual C++** à l'aide du modèle **Projet Win32** .

     Dans cette procédure pas à pas, le projet se nomme `RootFinder`.

     ![Création d’un projet Win32 C++](../test/media/utecpp05.png)

2.  Sélectionnez **DLL** et **Exporter les symboles** dans l'Assistant Application Win32.

     L'option **Exporter les symboles** génère une macro pratique qui permet de déclarer les méthodes exportées.

     ![Assistant de projet C++ défini pour les symboles DLL et d'exportation](../test/media/utecpp06.png)

3.  Déclarez une fonction exportée dans le fichier *.h* principal :

     ![Nouveau projet de code de la DLL et fichier .h avec macros API](../test/media/utecpp07.png)

     Le déclarateur `__declspec(dllexport)` permet que les membres publics et protégés de la classe soient visibles en dehors de la DLL. Pour plus d'informations, consultez [Utilisation de dllimport et dllexport dans les classes C++](/cpp/cpp/using-dllimport-and-dllexport-in-cpp-classes).

4.  Dans le fichier *.cpp* principal, ajoutez un corps minimal pour la fonction :

    ```cpp
        // Find the square root of a number.
        double CRootFinder::SquareRoot(double v)
        {
            return 0.0;
        }
    ```

##  <a name="make_functions_visible"></a> Associer le projet de test au projet DLL

1. Ajoutez le projet DLL aux références de projet du projet de test :

   1.  Ouvrez les propriétés du projet de test et choisissez **Propriétés communes** > **Framework et références**.

        ![Propriétés du projet C++ | Framework et références](../test/media/utecpp08.png)

   2.  Choisissez **Ajouter une nouvelle référence**.

        Dans la boîte de dialogue **Ajouter une référence** , sélectionnez le projet DLL et choisissez **Ajouter**.

        ![Propriétés du projet C++ | Ajouter une nouvelle référence](../test/media/utecpp09.png)

2. Dans le fichier *.cpp* de test unitaire principal, incluez le fichier *.h* du code de la DLL :

   ```cpp
   #include "..\RootFinder\RootFinder.h"
   ```

3. Ajoutez un test de base qui utilise la fonction exportée :

   ```cpp
   TEST_METHOD(BasicTest)
   {
      CRootFinder rooter;
      Assert::AreEqual(
         // Expected value:
         0.0,
         // Actual value:
         rooter.SquareRoot(0.0),
         // Tolerance:
         0.01,
        // Message:
        L"Basic test failed",
        // Line number - used if there is no PDB file:
        LINE_INFO());
   }
   ```

4. Générez la solution.

    Le nouveau test s’affiche dans **l’Explorateur de tests**.

5. Dans **l’Explorateur de tests**, choisissez **Exécuter tout**.

    ![Explorateur de tests unitaires &#45; Test de base réussi](../test/media/utecpp10.png)

   Vous avez configuré le test et les projets de code, et vérifié que vous pouviez exécuter des tests exécutant les fonctions du projet de code. Maintenant, vous pouvez commencer à écrire le code et les tests réels.

##  <a name="iterate"></a> Augmenter itérativement les tests et les faire réussir

1.  Ajoutez un nouveau test :

    ```cpp
    TEST_METHOD(RangeTest)
    {
      CRootFinder rooter;
      for (double v = 1e-6; v < 1e6; v = v * 3.2)
      {
        double actual = rooter.SquareRoot(v*v);
        Assert::AreEqual(v, actual, v/1000);
      }
    }
    ```

    > [!TIP]
    > Nous vous recommandons de ne pas modifier les tests ayant réussi. Ajoutez à la place un nouveau test, mettez à jour le code afin que le test réussisse, puis ajoutez un autre test, et ainsi de suite.
    >
    > Lorsque vos utilisateurs modifient leurs spécifications, désactivez les tests qui ne sont plus corrects. Écrivez de nouveaux tests et utilisez-les l'un après l'autre, de la même façon incrémentielle.

2.  Générez la solution, puis choisissez **Exécuter tout** dans **l’Explorateur de tests**.

     Le nouveau test échoue.

     ![RangeTest a échoué](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

    > [!TIP]
    > Vérifiez que chaque test échoue immédiatement après que vous l'avez écrit. Vous évitez ainsi de commettre l'erreur d'écrire un test qui n'échoue jamais.

3.  Améliorez le code de votre DLL afin que le nouveau test réussisse :

    ```cpp
    #include <math.h>
    ...
    double CRootFinder::SquareRoot(double v)
    {
      double result = v;
      double diff = v;
      while (diff > result/1000)
      {
        double oldResult = result;
        result = result - (result*result - v)/(2*result);
        diff = abs (oldResult - result);
      }
      return result;
    }
    ```

4.  Générez la solution, puis, dans **l’Explorateur de tests**, choisissez **Exécuter tout**.

     Les deux tests réussissent.

     ![Explorateur de tests unitaires &#45; Réussite du test de plage](../test/media/utecpp12.png)

    > [!TIP]
    > Développez le code en ajoutant les tests individuellement. Assurez-vous que tous les tests réussissent après chaque itération.

##  <a name="debug"></a> Déboguer un test ayant échoué

1.  Ajoutez un autre test :

    ```cpp
    #include <stdexcept>
    ...
    // Verify that negative inputs throw an exception.
    TEST_METHOD(NegativeRangeTest)
    {
      wchar_t message[200];
      CRootFinder rooter;
      for (double v = -0.1; v > -3.0; v = v - 0.5)
      {
        try
        {
          // Should raise an exception:
          double result = rooter.SquareRoot(v);

          _swprintf(message, L"No exception for input %g", v);
          Assert::Fail(message, LINE_INFO());
        }
        catch (std::out_of_range ex)
        {
          continue; // Correct exception.
        }
        catch (...)
        {
          _swprintf(message, L"Incorrect exception for %g", v);
          Assert::Fail(message, LINE_INFO());
        }
      }
    }
    ```

2.  Générez la solution et choisissez **Exécuter tout**.

3.  Ouvrez le test ayant échoué (ou double-cliquez dessus).

     L'échec d'assertion est mis en surbrillance. Le message d’échec est visible dans le volet de détails de **l’Explorateur de tests**.

     ![NegativeRangeTests, échec](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

4.  Pour voir pourquoi le test échoue, parcourez la fonction :

    1.  Définissez un point d'arrêt au début de la fonction SquareRoot.

    2.  Dans le menu contextuel du test ayant échoué, choisissez **Déboguer les tests sélectionnés**.

         Lorsque l'exécution s'arrête au point d'arrêt, parcourez le code.

5.  Insérez le code de la fonction que vous développez :

    ```cpp

    #include <stdexcept>
    ...
    double CRootFinder::SquareRoot(double v)
    {
        // Validate parameter:
        if (v < 0.0)
        {
          throw std::out_of_range("Can't do square roots of negatives");
        }

    ```

6.  Toutes les tests réussissent maintenant.

     ![Tous les tests sont concluants](../test/media/ute_ult_alltestspass.png)

> [!TIP]
> Si les tests individuels n’ont aucune dépendance qui les empêche d’être exécutés dans n’importe quel ordre, activez l’exécution parallèle des tests avec le bouton bascule ![UTE&#95;parallelicon&#45;small](../test/media/ute_parallelicon-small.png) dans la barre d’outils. Cela peut réduire sensiblement le temps nécessaire pour exécuter tous les tests.


##  <a name="refactor"></a> Refactoriser le code sans modifier les tests

1.  Simplifiez le calcul central de la fonction SquareRoot :

    ```cpp
    // old code:
    //   result = result - (result*result - v)/(2*result);
    // new code:
         result = (result + v/result)/2.0;

    ```

2.  Générez la solution et choisissez **Exécuter tout**, pour vous assurer que vous n'avez pas introduit d'erreur.

    > [!TIP]
    > Un bon jeu de tests unitaires vous garantit que vous n'avez pas introduit de bogues lors de la modification du code.
    >
    > Maintenez la refactorisation distincte des autres modifications.

## <a name="next-steps"></a>Étapes suivantes

-   **Isolement.** La plupart des DLL dépendent d'autres sous-systèmes tels que des bases de données et d'autres DLL. Ces autres composants sont souvent développés en parallèle. Pour permettre que le test unitaire soit exécuté pendant que les autres composants ne sont pas encore disponibles, vous devez remplacer

-   **Tests de vérification de build.** Des tests peuvent être effectués sur le serveur de builds de votre équipe à des intervalles définis. Cela garantit que les bogues ne sont pas introduits lors de l'intégration du travail de plusieurs membres de l'équipe.

-   **Tests d’archivage.** Vous pouvez imposer que certains tests soient effectués avant que chaque membre de l'équipe n'archive le code dans le contrôle de code source. Il s'agit généralement d'un sous-ensemble de l'ensemble complet des tests de vérification de build.

     Vous pouvez également imposer un niveau minimal de couverture du code.

## <a name="see-also"></a>Voir aussi

- [Ajouter des tests unitaires à des applications C++ existantes](../test/how-to-use-microsoft-test-framework-for-cpp.md)
- [Utilisation de Microsoft.VisualStudio.TestTools.CppUnitTestFramework](how-to-use-microsoft-test-framework-for-cpp.md)
- [Déboguer du code natif](../debugger/debugging-native-code.md)
- [Procédure pas à pas : création et utilisation d’une bibliothèque de liens dynamiques (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [Importation et exportation](/cpp/build/importing-and-exporting)
