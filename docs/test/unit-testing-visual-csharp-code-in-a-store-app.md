---
title: "Test unitaire du code Visual C# dans une application du Windows Store | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 23cb0d82-0451-464e-98ea-fa66e7010ead
caps.latest.revision: 19
author: "alexhomer1"
ms.author: "ahomer"
manager: "robinr"
caps.handback.revision: 19
---
# Test unitaire du code Visual C# dans une application du Windows Store
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique décrit une méthode permettant de créer des tests unitaires pour une classe Visual C\# dans une application du Windows Store.  La classe Rooter illustre de vagues souvenirs de la théorie de limite du calcul en implémentant une fonction qui calcule une estimation de la racine carrée d'un nombre donné.  L'application Maths peut ensuite utiliser cette fonction pour montrer à l'utilisateur les activités ludiques que l'on peut faire avec les mathématiques.  
  
 Cette rubrique explique comment utiliser le test unitaire comme première étape du développement.  Dans cette approche, vous écrivez d'abord une méthode de test qui vérifie un comportement spécifique dans le système que vous testez, puis vous écrivez le code qui réussit le test.  En modifiant l'ordre des procédures suivantes, vous pouvez inverser cette stratégie de manière à écrire d'abord le code que vous souhaitez tester, puis à écrire les tests unitaires.  
  
 Cette rubrique crée également une solution Visual Studio unique et des projets distincts pour les tests unitaires et la DLL que vous souhaitez tester.  Vous pouvez également inclure les tests unitaires directement dans le projet DLL, ou vous pouvez créer des solutions distinctes pour les tests unitaires et la DLL.  
  
> [!NOTE]
>  Visual Studio Community, Enterprise,  et Professional fournissent des fonctionnalités supplémentaires pour les tests unitaires.  
>   
>  -   Utilisez n'importe quelle infrastructure de test unitaire tierce et open source qui a créé un adaptateur complémentaire pour l'Explorateur de tests Microsoft.  Vous pouvez également analyser et afficher les informations de couverture du code pour les tests.  
> -   Exécutez vos tests après chaque build.  
> -   VS Enterprise contient également Microsoft Fakes, une infrastructure d'isolement pour le code managé qui vous permet de concentrer vos tests sur votre propre code en remplaçant le code de test pour les fonctionnalités système et tierces.  
>   
>  Pour plus d'informations, consultez [Vérification du code à l'aide de tests unitaires](http://msdn.microsoft.com/library/dd264975.aspx) dans MSDN Library.  
  
##  <a name="BKMK_In_this_topic"></a> Dans cette rubrique  
 [Créer la solution et le projet de test unitaire](#BKMK_Create_the_solution_and_the_unit_test_project)  
  
 [Vérifier l'exécution des tests dans l'explorateur de tests](#BKMK_Verify_that_the_tests_run_in_Test_Explorer)  
  
 [Ajouter la classe Rooter au projet Maths](#BKMK_Add_the_Rooter_class_to_the_Maths_project)  
  
 [Associer le projet de test au projet d'application](#BKMK_Couple_the_test_project_to_the_app_project)  
  
 [Augmenter itérativement les tests et les faire réussir](#BKMK_Iteratively_augment_the_tests_and_make_them_pass)  
  
 [Déboguer un test échoué](#BKMK_Debug_a_failing_test)  
  
 [Refactoriser le code](#BKMK_Refactor_the_code_)  
  
##  <a name="BKMK_Create_the_solution_and_the_unit_test_project"></a> Créer la solution et le projet de test unitaire  
  
1.  Dans le menu **Fichier**, choisissez **Nouveau**, puis **Nouveau projet**.  
  
2.  Dans la boîte de dialogue **Nouveau projet**, développez **Installé**, **Visual C\#**, puis choisissez **Windows Store**.  Choisissez ensuite **Application vide** dans la liste de modèles de projet.  
  
3.  Nommez le projet `Maths` et vérifiez que **Créer le répertoire pour la solution** est sélectionné.  
  
4.  Dans l'explorateur de solutions, sélectionnez le nom de la solution, **Ajouter** dans le menu contextuel, puis **Nouveau projet**.  
  
5.  Dans la boîte de dialogue **Nouveau projet**, développez **Installé**, puis développez **Visual C\#** et choisissez **Windows Store**.  Choisissez ensuite **Bibliothèque de tests unitaires \(applications Windows Store\)** dans la liste des modèles de projet.  
  
     ![Créer le projet de test unitaire](../test/media/ute_cs_windows_createunittestproject.png "UTE\_Cs\_windows\_CreateUnitTestProject")  
  
6.  Ouvrez UnitTest1.cs dans l'éditeur Visual Studio.  
  
    ```c#  
  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using Microsoft.VisualStudio.TestPlatform.UnitTestFramework;  
    using Maths;  
  
    namespace RooterTests  
    {  
        [TestClass]  
        public class UnitTest1  
  
            [TestMethod]  
            public void TestMethod1()  
            {  
  
            }  
  
    ```  
  
     Prenez note de ce qui suit :  
  
    1.  Chaque test est défini à l'aide de `[TestMethod]`.  Une méthode de test doit retourner void et ne contient pas de paramètres.  
  
    2.  Les méthodes de test doivent figurer dans une classe décorée avec l'attribut `[TestClass]`.  
  
         Lorsque les tests sont exécutés, une instance de chaque classe de test est créée.  Les méthodes de test sont appelées dans un ordre non défini.  
  
    3.  Vous pouvez définir des méthodes spéciales qui sont appelées avant et après chaque module, classe ou méthode.  Pour plus d'informations, consultez [Utilisation des membres Microsoft.VisualStudio.TestTools.UnitTesting dans les tests unitaires](../test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md) dans MSDN Library.  
  
##  <a name="BKMK_Verify_that_the_tests_run_in_Test_Explorer"></a> Vérifier l'exécution des tests dans l'explorateur de tests  
  
1.  Insérez du code de test dans `TestMethod1` du fichier **UnitTest1.cs** :  
  
    ```c#  
  
    [TestMethod]  
    public void TestMethod1()  
    {  
        Assert.AreEqual(0, 0);  
    }  
  
    ```  
  
     Notez que la classe `Assert` fournit plusieurs méthodes statiques que vous pouvez utiliser pour vérifier les résultats dans les méthodes de test.  
  
2.  Dans le menu **Test**, choisissez **Exécuter**, puis **Exécuter tout**.  
  
     Le projet de test est généré et exécuté.  La fenêtre de l'explorateur de tests s'affiche, et le test est répertorié sous **Tests réussis**.  Le volet de résumé situé au bas de la fenêtre fournit des informations supplémentaires sur le test sélectionné.  
  
     ![Explorateur de tests](../test/media/ute_cpp_testexplorer_testmethod1.png "UTE\_Cpp\_TestExplorer\_TestMethod1")  
  
##  <a name="BKMK_Add_the_Rooter_class_to_the_Maths_project"></a> Ajouter la classe Rooter au projet Maths  
  
1.  Dans l'explorateur de solutions, sélectionnez le nom de projet **Maths**.  Dans le menu contextuel, sélectionnez **Ajouter**, puis **Classe**.  
  
2.  Nommez le fichier de classe `Rooter.cs`.  
  
3.  Ajoutez le code suivant au fichier **Rooter.cs** de la classe Rooter :  
  
    ```c#  
  
    public Rooter()  
    {  
    }  
  
    // estimate the square root of a number  
    public double SquareRoot(double x)  
    {  
        return 0.0;  
    }  
  
    ```  
  
     La classe `Rooter` déclare un constructeur et la méthode d'estimation `SqareRoot`.  
  
4.  La méthode `SqareRoot` n'est qu'une implémentation minimale, qui est suffisante pour tester la structure de base de la configuration de test.  
  
##  <a name="BKMK_Couple_the_test_project_to_the_app_project"></a> Associer le projet de test au projet d'application  
  
1.  Ajoutez une référence de l'application Maths au projet RooterTests.  
  
    1.  Dans l'explorateur de solutions, sélectionnez le projet **RooterTests**, puis **Ajouter une référence...** dans le menu contextuel.  
  
    2.  Dans la boîte de dialogue **Ajouter une référence \- RooterTests**, développez **Solution**, puis choisissez **Projets**.  Sélectionnez ensuite l'élément **Maths**.  
  
         ![Ajouter une référence au projet Maths](../test/media/ute_cs_windows_addreference.png "UTE\_Cs\_windows\_AddReference")  
  
2.  Ajoutez une instruction using au fichier UnitTest1.cs :  
  
    1.  Ouvrez **UnitTest1.cs**.  
  
    2.  Ajoutez le code suivant sous la ligne `using Microsoft.VisualStudio.TestPlatform.UnitTestFramework;` :  
  
        ```c#  
        using Maths;  
        ```  
  
3.  Ajoutez un test qui utilise la fonction Rooter.  Ajoutez le code suivant à **UnitTest1.cpp** :  
  
    ```c#  
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
  
4.  Générez la solution.  
  
     Le nouveau test s'affiche dans l'explorateur de tests dans le nœud **Tests non exécutés**.  
  
5.  Dans l'explorateur de tests, sélectionnez **Exécuter tout**.  
  
     ![Test de base réussi](../test/media/ute_cpp_testexplorer_basictest.png "UTE\_Cpp\_TestExplorer\_BasicTest")  
  
 Vous avez configuré le test et les projets de code, et vérifié que vous pouviez exécuter des tests exécutant les fonctions du projet de code.  Maintenant, vous pouvez commencer à écrire le code et les tests réels.  
  
##  <a name="BKMK_Iteratively_augment_the_tests_and_make_them_pass"></a> Augmenter itérativement les tests et les faire réussir  
  
1.  Ajoutez un nouveau test :  
  
    ```c#  
    [TestMethod]  
    public void RangeTest()  
    {  
        Rooter rooter = new Rooter();  
        for (double v = 1e-6; v < 1e6; v = v * 3.2)  
        {  
            double expected = v;  
            double actual = rooter.SquareRoot(v*v);  
            double tolerance = ToleranceHelper(expected);  
            Assert.AreEqual(expected, actual, tolerance);  
        }  
    }  
  
    ```  
  
    > [!TIP]
    >  Nous vous recommandons de ne pas modifier les tests ayant réussi.  Ajoutez à la place un nouveau test, mettez à jour le code afin que le test réussisse, puis ajoutez un autre test, et ainsi de suite.  
    >   
    >  Lorsque vos utilisateurs modifient leurs spécifications, désactivez les tests qui ne sont plus corrects.  Écrivez de nouveaux tests et exécutez\-les individuellement, de la même façon incrémentielle.  
  
2.  Dans l'explorateur de tests, sélectionnez **Exécuter tout**.  
  
3.  Le test échoue.  
  
     ![RangeTest a échoué](../test/media/ute_cpp_testexplorer_rangetest_fail.png "UTE\_Cpp\_TestExplorer\_RangeTest\_Fail")  
  
    > [!TIP]
    >  Immédiatement après l'avoir écrit, vérifiez que chaque test échoue.  Vous évitez ainsi de commettre l'erreur d'écrire un test qui n'échoue jamais.  
  
4.  Améliorez le code testé afin que le nouveau test réussisse.  Remplacez la fonction `SqareRoot` dans **Rooter.cs** par ce qui suit :  
  
    ```c#  
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
  
5.  Générez la solution, puis sélectionnez **Exécuter tout** dans l'explorateur de tests.  
  
     Les trois tests réussissent maintenant.  
  
> [!TIP]
>  Développez le code en ajoutant les tests individuellement.  Assurez\-vous que tous les tests réussissent après chaque itération.  
  
##  <a name="BKMK_Debug_a_failing_test"></a> Déboguer un test échoué  
  
1.  Ajoutez un autre test à **UnitTest1.cs** :  
  
    ```c#  
    // Verify that negative inputs throw an exception.  
    [TestMethod]  
    public void NegativeRangeTest()  
    {  
        string message;  
        Rooter rooter = new Rooter();  
        for (double v = -0.1; v > -3.0; v = v - 0.5)  
        {  
            try  
            {  
                // Should raise an exception:  
                double actual = rooter.SquareRoot(v);  
  
                message = String.Format("No exception for input {0}", v);  
                Assert.Fail(message);  
            }  
            catch (ArgumentOutOfRangeException ex)  
            {  
                continue; // Correct exception.  
            }  
            catch (Exception e)  
            {  
                message = String.Format("Incorrect exception for {0}", v);  
                Assert.Fail(message);  
            }  
        }  
    }  
  
    ```  
  
2.  Dans l'explorateur de tests, sélectionnez **Exécuter tout**.  
  
     Le test échoue.  Sélectionnez le nom du test dans l'explorateur de tests.  L'échec d'assertion est mis en surbrillance.  Le message d'échec est visible dans le volet de détails de l'Explorateur de tests.  
  
     ![NegativeRangeTests, échec](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png "UTE\_Cpp\_TestExplorer\_NegativeRangeTest\_Fail")  
  
3.  Pour comprendre pourquoi le test échoue, parcourez la fonction :  
  
    1.  Définissez un point d'arrêt au début de la fonction `SquareRoot`.  
  
    2.  Dans le menu contextuel du test échoué, choisissez **Déboguer les tests sélectionnés**.  
  
         Lorsque l'exécution s'arrête au point d'arrêt, parcourez le code.  
  
    3.  Ajoutez le code à la méthode Rooter pour intercepter l'exception :  
  
        ```c#  
        public double SquareRoot(double x)  
        {  
            if (x < 0.0)  
            {  
                throw new ArgumentOutOfRangeException();  
        }  
  
        ```  
  
    1.  Dans l'explorateur de tests, sélectionnez **Exécuter tout** pour tester la méthode corrigée et vérifier que vous n'avez pas créé une régression.  
  
 Tous les tests réussissent maintenant.  
  
 ![Tous les tests sont concluants](../test/media/ute_ult_alltestspass.png "UTE\_ULT\_AllTestsPass")  
  
##  <a name="BKMK_Refactor_the_code_"></a> Refactoriser le code  
 **Simplifiez le calcul central dans la fonction SquareRoot.**  
  
1.  Modifiez l'implémentation du résultat.  
  
    ```c#  
    // old code  
    //result = result - (result*result - v)/(2*result);  
    // new code  
    result = (result + v/result) / 2.0;  
  
    ```  
  
2.  Choisissez **Exécuter tout** pour tester la méthode refactorisée et vérifier que vous n'avez pas créé une régression.  
  
> [!TIP]
>  Un ensemble stable de tests unitaires corrects est l'assurance que vous n'avez pas créé de bogues lors de la modification du code.  
  
 **Refactorisez le code de test pour supprimer le code dupliqué.**  
  
 Notez que la méthode `RangeTest` code en dur le dénominateur de la variable de tolérance utilisée dans la méthode `Assert`.  Si vous prévoyez d'ajouter des tests supplémentaires qui utilisent le même calcul de tolérance, l'utilisation d'une valeur codée en dur dans plusieurs emplacements peut provoquer des erreurs.  
  
1.  Ajoutez une méthode privée à la classe Unit1Test pour calculer la valeur de tolérance, puis appelez cette méthode à la place.  
  
    ```c#  
    private double ToleranceHelper(double expected)  
    {  
        return expected / 1000;  
    }  
  
    ...  
  
    [TestMethod]  
    public void RangeTest()  
    {  
        ...  
        // old code  
        // double tolerance = expected/1000;  
        // new code  
        double tolerance = ToleranceHelper(expected);  
        Assert.AreEqual(expected, actual, tolerance);  
    }  
    ...  
  
    ```  
  
2.  Choisissez **Exécuter tout** pour tester la méthode refactorisée et vérifier que vous n'avez pas créé une erreur.  
  
> [!NOTE]
>  Pour ajouter une méthode d'assistance à une classe de test, n'ajoutez pas l'attribut `[TestMethod]` à la méthode.  L'explorateur de tests n'enregistre pas la méthode à exécuter.