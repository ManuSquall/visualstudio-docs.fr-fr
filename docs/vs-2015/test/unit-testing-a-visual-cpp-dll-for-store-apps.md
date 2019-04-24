---
title: Test unitaire d’une DLL Visual C++ pour les applications du Windows Store | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 24afc90a-8774-4699-ab01-6602a7e6feb2
caps.latest.revision: 15
author: alexhomer1
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 716e6141d9f5ae76773a47b81ae54f5d7b70a9ec
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60104178"
---
# <a name="unit-testing-a-visual-c-dll-for-store-apps"></a>Test unitaire d’une DLL Visual C++ pour les applications du Windows Store
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette rubrique décrit une méthode permettant de créer des tests unitaires pour une DLL C++ pour des applications du Windows Store. La DLL RooterLib implémente une fonction qui calcule une estimation de la racine carrée d'un nombre donné. La DLL peut ensuite être incluse dans une application du Windows Store pour montrer à l'utilisateur les choses amusantes qu'il est possible de faire avec les mathématiques.  
  
 Cette rubrique vous montre comment utiliser les tests unitaires comme première étape du développement. Dans cette approche, vous écrivez d'abord une méthode de test qui vérifie un comportement spécifique dans le système que vous testez, puis vous écrivez le code qui réussit le test. En modifiant l'ordre des procédures suivantes, vous pouvez inverser cette stratégie de manière à écrire d'abord le code que vous souhaitez tester, puis à écrire les tests unitaires.  
  
 Cette rubrique crée également une solution Visual Studio unique et des projets distincts pour les tests unitaires et la DLL que vous souhaitez tester. Vous pouvez également inclure les tests unitaires directement dans le projet DLL, ou vous pouvez créer des solutions distinctes pour les tests unitaires et la DLL. Consultez la page [Ajout de tests unitaires aux applications C++ existantes](../test/unit-testing-existing-cpp-applications-with-test-explorer.md) pour obtenir des conseils sur la structure à utiliser.  
  
## <a name="BKMK_In_this_topic"></a> Dans cette rubrique  
 Cette rubrique contient les tâches suivantes :  
  
 [Créer la solution et le projet de test unitaire](#BKMK_Create_the_solution_and_the_unit_test_project)  
  
 [Vérifier que les tests s’exécutent dans l’Explorateur de tests](#BKMK_Verify_that_the_tests_run_in_Test_Explorer)  
  
 [Ajouter le projet DLL à la solution](#BKMK_Add_the_DLL_project_to_the_solution)  
  
 [Associer le projet de test au projet DLL](#BKMK_Couple_the_test_project_to_the_dll_project)  
  
 [Augmenter itérativement les tests et les faire réussir](#BKMK_Iteratively_augment_the_tests_and_make_them_pass)  
  
 [Déboguer un test non réussi](#BKMK_Debug_a_failing_test)  
  
 [Refactoriser le code sans modifier les tests](#BKMK_Refactor_the_code_without_changing_tests)  
  
## <a name="BKMK_Create_the_solution_and_the_unit_test_project"></a> Créer la solution et le projet de test unitaire  
  
1. Dans le menu **Fichier**, choisissez **Nouveau**, puis **Nouveau projet**.  
  
2. Dans la boîte de dialogue Nouveau projet, développez **Installé**, **Visual C++**, puis choisissez **Windows Store**. Choisissez ensuite **Bibliothèque de tests unitaires (applications du Windows Store)** dans la liste des modèles de projet.  
  
     ![Créer une bibliothèque de tests unitaires C&#43;&#43;](../test/media/ute-cpp-windows-unittestlib-create.png "UTE_Cpp_windows_UnitTestLib_Create")  
  
3. Nommez le projet `RooterLibTests`, spécifiez l’emplacement, nommez la solution `RooterLib`, puis vérifiez que la case **Créer le répertoire pour la solution** est cochée.  
  
     ![Spécifier la solution, le nom du projet et l’emplacement](../test/media/ute-cpp-windows-unittestlib-createspecs.png "UTE_Cpp_windows_UnitTestLib_CreateSpecs")  
  
4. Dans le nouveau projet, ouvrez **unittest1.cpp**.  
  
     ![unittest1.cpp](../test/media/ute-cpp-windows-unittest1-cpp.png "UTE_Cpp_windows_unittest1_cpp")  
  
     Prenez note de ce qui suit :  
  
    - Chaque test est défini à l'aide de `TEST_METHOD(YourTestName){...}`.  
  
         Vous n'avez pas à écrire une signature de fonction classique. La signature est créée par la macro TEST_METHOD. La macro génère une fonction d'instance qui retourne void. Elle génère également une fonction statique qui retourne des informations sur la méthode de test. Ces informations permettent à l'Explorateur de tests de trouver la méthode.  
  
    - Les méthodes de test sont regroupées en classes à l'aide de `TEST_CLASS(YourClassName){...}`.  
  
         Lorsque les tests sont exécutés, une instance de chaque classe de test est créée. Les méthodes de test sont appelées dans un ordre non défini. Vous pouvez définir des méthodes spéciales qui sont appelées avant et après chaque module, classe ou méthode. Pour plus d’informations, consultez [Utilisation de Microsoft.VisualStudio.TestTools.CppUnitTestFramework](../test/using-microsoft-visualstudio-testtools-cppunittestframework.md) dans MSDN Library.  
  
## <a name="BKMK_Verify_that_the_tests_run_in_Test_Explorer"></a> Vérifier que les tests s’exécutent dans l’Explorateur de tests  
  
1. Insérez le code de test :  
  
    ```cpp  
    TEST_METHOD(TestMethod1)  
    {  
        Assert::AreEqual(1,1);  
    }  
    ```  
  
     Notez que la classe `Assert` fournit plusieurs méthodes statiques que vous pouvez utiliser pour vérifier les résultats dans les méthodes de test.  
  
2. Dans le menu **Test**, choisissez **Exécuter**, puis **Exécuter tout**.  
  
     Le projet de test est généré et exécuté. La fenêtre de l’Explorateur de tests s’affiche, et le test est listé sous **Tests réussis**. Le volet de résumé situé au bas de la fenêtre fournit des informations supplémentaires sur le test sélectionné.  
  
     ![Explorateur de tests](../test/media/ute-cpp-testexplorer-testmethod1.png "UTE_Cpp_TestExplorer_TestMethod1")  
  
## <a name="BKMK_Add_the_DLL_project_to_the_solution"></a> Ajouter le projet DLL à la solution  
  
1. Dans l'Explorateur de solutions, choisissez le nom de la solution. Dans le menu contextuel, choisissez **Ajouter**, puis **Ajouter un nouveau projet**.  
  
     ![Créer le projet RooterLib](../test/media/ute-cpp-windows-rooterlib-create.png "UTE_Cpp_windows_RooterLib_Create")  
  
2. Dans la boîte de dialogue **Ajouter un nouveau projet**, choisissez **DLL (applications du Windows Store)**.  
  
3. Ajoutez le code suivant au fichier **RooterLib.h** :  
  
    ```cpp  
    // The following ifdef block is the standard way of creating macros which make exporting   
    // from a DLL simpler. All files within this DLL are compiled with the ROOTERLIB_EXPORTS  
    // symbol defined on the command line. This symbol should not be defined on any project  
    // that uses this DLL. This way any other project whose source files include this file see   
    // ROOTERLIB_API functions as being imported from a DLL, whereas this DLL sees symbols  
    // defined with this macro as being exported.  
    #ifdef ROOTERLIB_EXPORTS  
    #define ROOTERLIB_API  __declspec(dllexport)  
    #else  
    #define ROOTERLIB_API __declspec(dllimport)  
    #endif //ROOTERLIB_EXPORTS  
  
    class ROOTERLIB_API CRooterLib {  
    public:  
        CRooterLib(void);  
        double SquareRoot(double v);  
    };  
    ```  
  
     Les commentaires expliquent la signification du bloc ifdef non seulement au développeur de la DLL, mais aussi à toute personne qui référence la DLL dans son projet. Vous pouvez ajouter le symbole ROOTERLIB_EXPORTS à la ligne de commande en utilisant les propriétés du projet de la DLL.  
  
     La classe `CRooterLib` déclare un constructeur et la méthode d'estimation `SqareRoot`.  
  
4. Ajoutez le symbole ROOTERLIB_EXPORTS à la ligne de commande.  
  
    1. Dans l’Explorateur de solutions, choisissez le projet **RooterLib**, puis **Propriétés** dans le menu contextuel.  
  
         ![Ajouter la définition d’un symbole de préprocesseur](../test/media/ute-cpp-windows-addpreprocessorsymbol.png "UTE_Cpp_windows_AddPreprocessorSymbol")  
  
    2. Dans la boîte de dialogue Page de propriétés de RooterLib, développez **Propriétés de configuration**, **C++**, puis choisissez **Préprocesseur**.  
  
    3. Choisissez **\<Modifier>** dans la liste **Définitions de préprocesseur**, puis ajoutez `ROOTERLIB_EXPORTS` dans la boîte de dialogue Définitions de préprocesseur.  
  
5. Ajoutez des implémentations minimales des fonctions déclarées. Ouvrez **RooterLib.cpp**, puis ajoutez le code suivant :  
  
    ```  
    // constructor  
    CRooterLib::CRooterLib()  
    {  
    }  
  
    // Find the square root of a number.  
    double CRooterLib::SquareRoot(double v)  
    {  
        return 0.0;  
    }  
  
    ```  
  
## <a name="BKMK_Couple_the_test_project_to_the_dll_project"></a> Associer le projet de test au projet DLL  
  
1. Ajoutez RooterLib au projet RooterLibTests.  
  
   1. Dans l’Explorateur de solutions, choisissez le projet **RooterLibTests**, puis **Références** dans le menu contextuel.  
  
   2. Dans la boîte de dialogue Propriétés du projet RooterLib, développez **Propriétés communes**, puis choisissez **Framework et références**.  
  
   3. Choisissez **Ajouter une nouvelle référence**.  
  
   4. Dans la boîte de dialogue **Ajouter une référence**, développez **Solution**, puis choisissez **Projets**. Sélectionnez ensuite l’élément **RouterLib**.  
  
2. Incluez le fichier d’en-tête RooterLib dans **unittest1.cpp**.  
  
   1. Ouvrez **unittest1.cpp**.  
  
   2. Ajoutez le code suivant sous la ligne `#include "CppUnitTest.h"` :  
  
       ```cpp  
       #include "..\RooterLib\RooterLib.h"  
       ```  
  
3. Ajoutez un test qui utilise la fonction importée. Ajoutez le code suivant à **unittest1.cpp** :  
  
   ```  
   TEST_METHOD(BasicTest)  
   {  
       CRooterLib rooter;  
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
  
    Le nouveau test s’affiche dans l’Explorateur de tests, dans le nœud **Tests non exécutés**.  
  
5. Dans l'Explorateur de tests, choisissez **Exécuter tout**.  
  
    ![Test de base réussi](../test/media/ute-cpp-testexplorer-basictest.png "UTE_Cpp_TestExplorer_BasicTest")  
  
   Vous avez configuré le test et les projets de code, et vérifié que vous pouviez exécuter des tests exécutant les fonctions du projet de code. Maintenant, vous pouvez commencer à écrire le code et les tests réels.  
  
## <a name="BKMK_Iteratively_augment_the_tests_and_make_them_pass"></a> Augmenter itérativement les tests et les faire réussir  
  
1. Ajoutez un nouveau test :  
  
    ```  
    TEST_METHOD(RangeTest)  
    {  
        CRooterLib rooter;  
        for (double v = 1e-6; v < 1e6; v = v * 3.2)  
        {  
            double expected = v;  
            double actual = rooter.SquareRoot(v*v);  
            double tolerance = expected/1000;  
            Assert::AreEqual(expected, actual, tolerance);  
        }  
    };  
  
    ```  
  
    > [!TIP]
    >  Nous vous recommandons de ne pas modifier les tests ayant réussi. Ajoutez à la place un nouveau test, mettez à jour le code afin que le test réussisse, puis ajoutez un autre test, et ainsi de suite.  
    >   
    >  Lorsque vos utilisateurs modifient leurs spécifications, désactivez les tests qui ne sont plus corrects. Écrivez de nouveaux tests et utilisez-les l'un après l'autre, de la même façon incrémentielle.  
  
2. Dans l'Explorateur de tests, choisissez **Exécuter tout**.  
  
3. Le test échoue.  
  
     ![Échec de RangeTest](../test/media/ute-cpp-testexplorer-rangetest-fail.png "UTE_Cpp_TestExplorer_RangeTest_Fail")  
  
    > [!TIP]
    >  Vérifiez que chaque test échoue immédiatement après que vous l'avez écrit. Vous évitez ainsi de commettre l'erreur d'écrire un test qui n'échoue jamais.  
  
4. Améliorez le code testé afin que le nouveau test réussisse. Ajoutez ce qui suit à **RooterLib.cpp** :  
  
    ```cpp  
    #include <math.h>  
    ...  
    // Find the square root of a number.  
    double CRooterLib::SquareRoot(double v)  
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
  
5. Générez la solution, puis, dans l'Explorateur de tests, choisissez **Exécuter tout**.  
  
     Les deux tests réussissent.  
  
> [!TIP]
>  Développez le code en ajoutant les tests individuellement. Assurez-vous que tous les tests réussissent après chaque itération.  
  
## <a name="BKMK_Debug_a_failing_test"></a> Déboguer un test ayant échoué  
  
1. Ajoutez un autre test à **unittest1.cpp** :  
  
   ```  
   // Verify that negative inputs throw an exception.  
    TEST_METHOD(NegativeRangeTest)  
    {  
      wchar_t message[200];  
      CRooterLib rooter;  
      for (double v = -0.1; v > -3.0; v = v - 0.5)  
      {  
        try   
        {  
          // Should raise an exception:  
          double result = rooter.SquareRoot(v);  
  
          swprintf_s(message, L"No exception for input %g", v);  
          Assert::Fail(message, LINE_INFO());  
        }  
        catch (std::out_of_range ex)  
        {  
          continue; // Correct exception.  
        }  
        catch (...)  
        {  
          swprintf_s(message, L"Incorrect exception for %g", v);  
          Assert::Fail(message, LINE_INFO());  
        }  
      }  
   };  
  
   ```  
  
2. Dans l'Explorateur de tests, choisissez **Exécuter tout**.  
  
    Le test échoue. Sélectionnez le nom du test dans l'explorateur de tests. L'échec d'assertion est mis en surbrillance. Le message d'échec est visible dans le volet de détails de l'Explorateur de tests.  
  
    ![Échec de NegativeRangeTests](../test/media/ute-cpp-testexplorer-negativerangetest-fail.png "UTE_Cpp_TestExplorer_NegativeRangeTest_Fail")  
  
3. Pour voir pourquoi le test échoue, parcourez la fonction :  
  
   1. Définissez un point d'arrêt au début de la fonction `SquareRoot`.  
  
   2. Dans le menu contextuel du test ayant échoué, choisissez **Déboguer les tests sélectionnés**.  
  
        Lorsque l'exécution s'arrête au point d'arrêt, parcourez le code.  
  
   3. Ajoutez du code à **RooterLib.cpp** pour intercepter l’exception :  
  
       ```  
       #include <stdexcept>  
       ...  
       double CRooterLib::SquareRoot(double v)  
       {  
           //Validate the input parameter:  
           if (v < 0.0)   
           {  
             throw std::out_of_range("Can't do square roots of negatives");  
           }  
       ...  
  
       ```  
  
   1. Dans l’Explorateur de tests, choisissez **Exécuter tout** pour tester la méthode corrigée et vérifier que vous n’avez pas introduit une régression.  
  
   Toutes les tests réussissent maintenant.  
  
   ![Tous les tests sont concluants](../test/media/ute-ult-alltestspass.png "UTE_ULT_AllTestsPass")  
  
## <a name="BKMK_Refactor_the_code_without_changing_tests"></a> Refactoriser le code sans modifier les tests  
  
1. Simplifiez le calcul central dans la fonction `SquareRoot` :  
  
    ```  
    // old code  
    //result = result - (result*result - v)/(2*result);  
    // new code  
    result = (result + v/result) / 2.0;  
  
    ```  
  
2. Choisissez **Exécuter tout** pour tester la méthode refactorisée et vérifier que vous n’avez pas introduit une régression.  
  
    > [!TIP]
    >  Un ensemble stable de tests unitaires corrects est l'assurance que vous n'avez pas créé de bogues lors de la modification du code.  
    >   
    >  Maintenez la refactorisation distincte des autres modifications.
