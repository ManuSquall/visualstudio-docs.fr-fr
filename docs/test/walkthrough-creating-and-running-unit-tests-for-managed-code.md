---
title: "Procédure pas à pas : création et exécution de tests unitaires pour le code managé | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.assetid: 2b018b18-b412-4e0e-b0ee-b580a2f3ba9c
caps.latest.revision: "83"
ms.author: douge
manager: douge
ms.workload: dotnet
ms.openlocfilehash: ebdac762d3dcc4079ed6e8247b394da685b1013a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-and-running-unit-tests-for-managed-code"></a>Procédure pas à pas : création et exécution de tests unitaires pour le code managé
Cette procédure pas à pas décrit la création, l’exécution et la personnalisation d’une série de tests unitaires à l’aide du framework de tests unitaires Microsoft pour le code managé et de l’explorateur de tests de Visual Studio. Vous commencez avec un projet C# qui est en développement, vous créez des tests qui utilisent son code, vous exécutez les tests et vous examinez les résultats. Ensuite, vous pouvez modifier le code de votre projet et réexécuter les tests.  
  
 Cette rubrique contient les sections suivantes :  
  
 [Préparation de la procédure pas à pas](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Prepare_the_walkthrough)  
  
 [Créer un projet de test unitaire](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_a_unit_test_project)  
  
 [Créer la classe de test](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_the_test_class)  
  
-   [Spécifications de la classe de test](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Test_class_requirements)  
  
 [Créer la première méthode de test](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_the_first_test_method)  
  
-   [Spécifications des méthodes de test](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Test_method_requirements)  
  
 [Générer et exécuter le test](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Build_and_run_the_test)  
  
 [Vérifier votre code et exécuter à nouveau vos tests](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Fix_your_code_and_rerun_your_tests)  
  
 [Utiliser les tests unitaires pour améliorer votre code](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Use_unit_tests_to_improve_your_code)  
  
> [!NOTE]
>  Cette procédure pas à pas utilise le framework de tests unitaires Microsoft pour le code managé. L’explorateur de tests peut également exécuter des tests depuis des frameworks de tests unitaires tiers qui ont des adaptateurs pour l’explorateur de tests. Pour plus d’informations, consultez [Installer des frameworks de tests unitaires tiers](../test/install-third-party-unit-test-frameworks.md)  
  
> [!NOTE]
>  Pour plus d’informations sur la façon d’exécuter des tests à partir d’une ligne de commande, consultez [Procédure pas à pas : utilisation de l’utilitaire de test de ligne de commande](http://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867).  
  
## <a name="prerequisites"></a>Prérequis  
  
-   Le projet Bank. Consultez [Exemple de projet pour la création de tests unitaires](../test/sample-project-for-creating-unit-tests.md).  
  
##  <a name="BKMK_Prepare_the_walkthrough"></a> Préparer la procédure pas à pas  
  
1.  Ouvrez Visual Studio.  
  
2.  Dans le menu **Fichier** , pointez sur **Nouveau** , puis cliquez sur **Projet**.  
  
     La boîte de dialogue **Nouveau projet** s’affiche.  
  
3.  Sous **Modèles installés**, cliquez sur **Visual C#**.  
  
4.  Dans la liste de types d’applications, cliquez sur **Bibliothèque de classes**.  
  
5.  Dans la zone **Nom** , tapez `Bank` , puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Si le nom « Bank » est déjà utilisé, choisissez un autre nom pour le projet.  
  
     Le nouveau projet Bank est créé et affiché dans l’Explorateur de solutions, avec le fichier Class1.cs ouvert dans l’éditeur de code.  
  
    > [!NOTE]
    >  Si le fichier Class1.cs n’est pas ouvert dans l’éditeur de code, double-cliquez sur ce fichier dans l’Explorateur de solutions pour l’ouvrir.  
  
6.  Copiez le code source de l’[Exemple de projet pour la création de tests unitaires](../test/sample-project-for-creating-unit-tests.md).  
  
7.  Remplacez le contenu d’origine de Class1.cs par le code de l’[Exemple de projet pour la création de tests unitaires](../test/sample-project-for-creating-unit-tests.md).  
  
8.  Enregistrez le fichier avec le nom BankAccount.cs  
  
9. Dans le menu **Générer** , cliquez sur **Générer la solution**.  
  
 Vous avez maintenant un projet nommé Bank. Il contient le code source à tester et des outils avec lesquels le tester. L’espace de noms pour Bank, **BankAccountNS**, contient la classe publique **BankAccount**, dont vous testerez les méthodes dans les procédures suivantes.  
  
 Dans ce démarrage rapide, nous nous concentrons sur la méthode `Debit` . Cette méthode est appelée quand de l’argent est retiré d’un compte et contient le code suivant :  
  
```csharp  
// method under test  
public void Debit(double amount)  
{  
    if(amount > m_balance)  
    {  
        throw new ArgumentOutOfRangeException("amount");  
    }  
    if (amount < 0)  
    {  
        throw new ArgumentOutOfRangeException("amount");  
    }  
    m_balance += amount;  
}  
  
```  
  
##  <a name="BKMK_Create_a_unit_test_project"></a> Créer un projet de test unitaire  
 **Condition préalable**: suivez les étapes de la procédure [Prepare the walkthrough](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Prepare_the_walkthrough).  
  
#### <a name="to-create-a-unit-test-project"></a>Pour créer un projet de test unitaire  
  
1.  Dans le menu **Fichier** , choisissez **Ajouter**, puis **Nouveau projet...**.  
  
2.  Dans la boîte de dialogue Nouveau Projet, développez **Installé**, développez **Visual C#**, puis choisissez **Test**.  
  
3.  Dans la liste des modèles, sélectionnez **Projet de test unitaire**.  
  
4.  Dans la zone **Nom** , entrez BankTests, puis choisissez **OK**.  
  
     Le projet **BankTests** est ajouté à la solution **Bank** .  
  
5.  Dans le projet **BankTests** , ajoutez une référence à la solution **Bank** .  
  
     Dans l’Explorateur de solutions, sélectionnez **Références** dans le projet **BankTests** puis choisissez **Ajouter une référence…** dans le menu contextuel.  
  
6.  Dans la boîte de dialogue Gestionnaire de références, développez **Solution** puis cochez l’élément **Bank** .  
  
##  <a name="BKMK_Create_the_test_class"></a> Créer la classe de test  
 Nous avons besoin d’une classe de test pour vérifier la classe `BankAccount` . Nous pouvons utiliser UnitTest1.cs qui a été généré par le modèle de projet, mais nous devons donner au fichier et à la classe des noms plus descriptifs. Nous pouvons effectuer cela en une seule étape en renommant le fichier dans l’Explorateur de solutions.  
  
 **Changement du nom d’un fichier de classe**  
  
 Dans l’Explorateur de solutions, sélectionnez le fichier UnitTest1.cs dans le projet BankTests. Dans le menu contextuel, choisissez **Renommer**, puis renommez le fichier BankAccountTests.cs. Choisissez **Oui** dans la boîte de dialogue qui vous demande si vous souhaitez remplacer le nom de toutes les références du projet par « UnitTest1 ». Cette opération a pour effet de remplacer le nom de la classe par `BankAccountTest`.  
  
 Le fichier BankAccountTests.cs contient maintenant le code suivant :  
  
```csharp  
// unit test code  
using System;  
using Microsoft.VisualStudio.TestTools.UnitTesting;  
  
namespace BankTests  
{  
    [TestClass]  
    public class BankAccountTests  
    {  
        [TestMethod]  
        public void TestMethod1()  
        {  
        }  
    }  
}  
```  
  
 **Ajouter une instruction using au projet testé**  
  
 Nous pouvons également ajouter une instruction using à la classe pour nous permettre d’appeler le projet testé sans utiliser de noms qualifiés complets. En haut du fichier de classe, ajoutez :  
  
```csharp  
using BankAccountNS;  
```  
  
###  <a name="BKMK_Test_class_requirements"></a> Spécifications de la classe de test  
 La configuration minimale requise pour une classe de test est la suivante :  
  
-   L’attribut `[TestClass]` est requis dans le framework de tests unitaires Microsoft pour le code managé pour toute classe qui contient les méthodes de test unitaire à exécuter dans l’explorateur de tests.  
  
-   Chaque méthode de test à exécuter avec l’explorateur de tests doit avoir l’attribut `[TestMethod]`.  
  
 Vous pouvez avoir d’autres classes dans un projet de test unitaire qui n’ont pas l’attribut `[TestClass]` , et vous pouvez avoir d’autres méthodes dans les classes de test qui n’ont pas l’attribut `[TestMethod]` . Vous pouvez utiliser ces autres classes et méthodes dans vos méthodes de test.  
  
##  <a name="BKMK_Create_the_first_test_method"></a> Créer la première méthode de test  
 Dans cette procédure, nous écrirons des méthodes de test unitaire pour vérifier le comportement de la méthode `Debit` de la classe `BankAccount` . La méthode est répertoriée ci-dessus.  
  
 En analysant la méthode testée, nous déterminons qu’il existe au moins trois comportements qui doivent être vérifiés :  
  
1.  La méthode lève une exception <xref:System.ArgumentOutOfRangeException> si le montant du débit est supérieur au solde.  
  
2.  Elle lève également l’exception `ArgumentOutOfRangeException` si le montant du débit est inférieur à zéro.  
  
3.  Si les contrôles en 1.) et 2.) sont satisfaisants, la méthode soustrait le montant du solde du compte.  
  
 Dans notre premier test, nous vérifions qu’un montant valide (inférieur au solde du compte et supérieur à zéro) retire le montant approprié du compte.  
  
#### <a name="to-create-a-test-method"></a>Pour créer une méthode de test  
  
1.  Ajoutez une instruction using `BankAccountNS;` au fichier BankAccountTests.cs.  
  
2.  Ajoutez la méthode suivante à cette classe `BankAccountTests` :  
  
    ```csharp  
    // unit test code  
    [TestMethod]  
    public void Debit_WithValidAmount_UpdatesBalance()  
    {  
        // arrange  
        double beginningBalance = 11.99;  
        double debitAmount = 4.55;  
        double expected = 7.44;  
        BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);  
  
        // act  
        account.Debit(debitAmount);  
  
        // assert  
        double actual = account.Balance;  
        Assert.AreEqual(expected, actual, 0.001, "Account not debited correctly");  
    }  
    ```  
  
 La méthode est plutôt simple. Nous mettons en place un nouvel objet `BankAccount` avec un solde de début, puis nous retirons un montant valide. Nous utilisons la méthode du framework de tests unitaires Microsoft pour le code managé <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A> pour vérifier que le solde de fin correspond à ce que nous attendions.  
  
###  <a name="BKMK_Test_method_requirements"></a> Spécifications des méthodes de test  
 Une méthode de test doit répondre aux spécifications suivantes :  
  
-   La méthode doit être décorée avec l’attribut `[TestMethod]` .  
  
-   La méthode doit retourner `void`.  
  
-   La méthode ne peut pas avoir de paramètres.  
  
##  <a name="BKMK_Build_and_run_the_test"></a> Générer et exécuter le test  
  
#### <a name="to-build-and-run-the-test"></a>Pour générer et exécuter le test  
  
1.  Dans le menu **Générer** , choisissez **Générer la solution**.  
  
     En l’absence d’erreurs, la fenêtre UnitTestExplorer apparaît avec **Debit_WithValidAmount_UpdatesBalance** répertorié dans le groupe **Tests non exécutés** . Si l’explorateur de tests n’apparaît pas après une génération réussie, sélectionnez **Test** dans le menu, puis **Fenêtres**, puis  **Explorateur de tests**.  
  
2.  Sélectionnez **Exécuter tout** pour exécuter le test. Pendant que le test s’exécute, la barre d’état en haut de la fenêtre s’anime. À l’issue de la série de tests, la barre devient verte si toutes les méthodes de test ont réussi, ou rouge si l’un des tests a échoué.  
  
3.  Dans ce cas, le test échoue. La méthode de test est déplacée vers le groupe **Échecs de tests** . Sélectionnez la méthode dans l’explorateur de tests pour en afficher les détails en bas de la fenêtre.  
  
##  <a name="BKMK_Fix_your_code_and_rerun_your_tests"></a> Vérifier votre code et exécuter à nouveau vos tests  
 **Analyser les résultats des tests**  
  
 Le résultat de test contient un message qui décrit l’échec. Pour la méthode `AreEquals`, un message affiche ce qui était attendu (le paramètre **Expected\<*XXX*>**) et ce qui a été reçu réellement (le paramètre **Actual\<*YYY*>**). Nous nous attendions à ce que le solde décline par rapport au solde de début, mais il a plutôt augmenté du montant du retrait.  
  
 Un réexamen du code Debit indique que le test unitaire a réussi à trouver un bogue. Le montant du retrait est ajouté au solde du compte quand il doit être soustrait.  
  
 **Corriger le bogue**  
  
 Pour corriger l’erreur, remplacez simplement la ligne  
  
```csharp  
m_balance += amount;  
```  
  
 par  
  
```csharp  
m_balance -= amount;  
```  
  
 **Réexécuter le test**  
  
 Dans l’explorateur de tests, choisissez **Exécuter tout** pour réexécuter le test. La barre rouge/verte devient verte, et le test est déplacé vers le groupe **Tests réussis** .  
  
##  <a name="BKMK_Use_unit_tests_to_improve_your_code"></a> Utiliser les tests unitaires pour améliorer votre code  
 Cette section décrit comment un processus itératif d’analyse, de développement de test unitaire et de refactorisation peut vous aider à rendre votre code de production plus fiable et efficace.  
  
 **Analyser les problèmes**  
  
 Après avoir créé une méthode de test pour vérifier qu’un montant valide est correctement déduit dans la méthode `Debit` , nous pouvons nous tourner vers les cas restants dans notre analyse d’origine :  
  
1.  La méthode lève une exception `ArgumentOutOfRangeException` si le montant du débit est supérieur au solde.  
  
2.  Elle lève également l’exception `ArgumentOutOfRangeException` si le montant du débit est inférieur à zéro.  
  
 **Créer les méthodes de test**  
  
 Une première tentative de création d’une méthode de test pour résoudre ces problèmes semble prometteuse :  
  
```csharp  
//unit test method  
[TestMethod]  
[ExpectedException(typeof(ArgumentOutOfRangeException))]  
public void Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange()  
{  
    // arrange  
    double beginningBalance = 11.99;  
    double debitAmount = -100.00;  
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);  
  
    // act  
    account.Debit(debitAmount);  
  
    // assert is handled by ExpectedException  
}  
  
```  
  
 Nous utilisons l’attribut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> pour déclarer que la bonne exception a été levée. L’attribut entraîne l’échec du test à moins qu’une exception `ArgumentOutOfRangeException` ne soit levée. L’exécution du test avec à la fois les valeurs `debitAmount` positives et négatives puis en modifiant temporairement la méthode testée pour lever une exception <xref:System.ApplicationException> générique quand le montant est inférieur à zéro indique que le test se comporte correctement. Pour tester le cas où le montant retiré est supérieur au solde, il suffit d’effectuer les opérations suivantes :  
  
1.  Créez une méthode de test nommée `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`.  
  
2.  Copiez le corps de la méthode depuis `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` vers la nouvelle méthode.  
  
3.  Définissez `debitAmount` sur un nombre supérieur au solde.  
  
 **Exécuter les tests**  
  
 L’exécution des deux méthodes avec des valeurs différentes pour `debitAmount` montre que les tests gèrent correctement nos cas restants. L’exécution des trois tests confirme que tous les cas présents dans notre analyse d’origine sont traités correctement.  
  
 **Poursuivre l’analyse**  
  
 Toutefois, les deux dernières méthodes de test sont également quelque peu troublantes. Nous ne pouvons pas être certains de la condition du code qui lève une exception quand l’un ou l’autre des tests est exécuté. Un moyen de faire la différence entre les deux conditions serait utile. Quand nous réfléchissons au problème, il devient clair que l’identification de la condition qui n’a pas été respectée augmenterait notre confiance dans les tests. Ces informations seraient également très probablement utiles pour le mécanisme de production qui gère l’exception quand elle est levée par la méthode testée. La génération d’informations supplémentaires quand la méthode lève une exception aiderait tous les éléments concernés, mais l’attribut `ExpectedException` ne peut pas fournir ces informations.  
  
 En examinant encore la méthode testée, nous constatons que les deux instructions conditionnelles utilisent un constructeur `ArgumentOutOfRangeException` qui accepte le nom de l’argument comme paramètre :  
  
```csharp  
throw new ArgumentOutOfRangeException("amount");  
```  
  
 En effectuant des recherches dans MSDN Library, nous découvrons qu’il existe un constructeur qui génère des informations bien plus élaborées. <xref:System.ArgumentOutOfRangeException.%23ctor%2A>`(String, Object, String)` inclut le nom de l’argument, la valeur de l’argument et un message défini par l’utilisateur. Nous pouvons refactoriser la méthode testée pour utiliser ce constructeur. Encore mieux, nous pouvons utiliser les membres de type disponibles publiquement pour spécifier les erreurs.  
  
 **Refactoriser le code testé**  
  
 Nous définissons d’abord deux constantes pour les messages d’erreur au niveau de la portée d’une classe :  
  
```csharp  
// class under test  
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";  
public const string DebitAmountLessThanZeroMessage = "Debit amount less than zero";  
```  
  
 Nous modifions ensuite les deux instructions conditionnelles dans la méthode `Debit` :  
  
```csharp  
// method under test  
// ...  
    if (amount > m_balance)  
    {  
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountExceedsBalanceMessage);  
    }  
  
    if (amount < 0)  
    {  
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountLessThanZeroMessage);  
    }  
// ...  
```  
  
 **Refactoriser les méthodes de test**  
  
 Dans notre méthode de test, nous commençons par supprimer l’attribut `ExpectedException` . À sa place, nous interceptons l’exception levée et vérifions qu’elle a été levée dans l’instruction de condition appropriée. Toutefois, nous devons maintenant choisir entre deux options pour vérifier nos conditions restantes. Par exemple, dans la méthode `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` , nous pouvons effectuer l’une des actions suivantes :  
  
-   Déclarer que la propriété `ActualValue` de l’exception (le deuxième paramètre du constructeur `ArgumentOutOfRangeException` ) est supérieure au solde de début. Cette option nécessite de tester la propriété `ActualValue` de l’exception par rapport à la variable `beginningBalance` de la méthode de test, mais aussi de vérifier que la propriété `ActualValue` est supérieure à zéro.  
  
-   Déclarer que le message (le troisième paramètre du constructeur) inclut le `DebitAmountExceedsBalanceMessage` défini dans la classe `BankAccount` .  
  
 La méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName> dans le framework de tests unitaires Microsoft nous permet de vérifier la deuxième option sans les calculs requis par la première option.  
  
 Une deuxième tentative de révision de `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` pourrait ressembler à :  
  
```csharp  
[TestMethod]  
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()  
{  
    // arrange  
    double beginningBalance = 11.99;  
    double debitAmount = 20.0;  
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);  
  
    // act  
    try  
    {  
        account.Debit(debitAmount);  
    }  
    catch (ArgumentOutOfRangeException e)  
    {  
        // assert  
        StringAssert.Contains(e.Message, BankAccount. DebitAmountExceedsBalanceMessage);  
    }  
}  
```  
  
 **Retester, réécrire et réanalyser**  
  
 Lorsque nous retestons les méthodes de test avec des valeurs différentes, nous obtenons les informations suivantes :  
  
1.  Si nous interceptons l’erreur correcte à l’aide d’une  assertion où `debitAmount` est supérieur au solde, l’assertion `Contains` passe, l’exception est ignorée et la méthode de test passe alors. Il s’agit du comportement que nous souhaitons.  
  
2.  Si nous utilisons un `debitAmount` inférieur à 0, l’assertion échoue, car un message d’erreur inapproprié est retourné. L’assertion échoue également si nous introduisons une exception `ArgumentOutOfRange` temporaire à un autre point dans le chemin de code de la méthode testée. Cela aussi est approprié.  
  
3.  Si la valeur de `debitAmount` est valide (autrement dit, inférieure au solde mais supérieure à zéro), aucune exception n’est interceptée et l’assertion n’est donc jamais interceptée. La méthode de test réussit. Cela ne convient pas, car nous souhaitons que la méthode de test échoue si aucune exception n’est levée.  
  
 Le troisième fait est un bogue dans notre méthode de test. Pour essayer de résoudre le problème, nous ajoutons une assertion <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> à la fin de la méthode de test pour gérer le cas où aucune exception n’est levée.  
  
 Cependant, un nouveau test montre que le test échoue maintenant si l’exception correcte est interceptée. L’instruction catch réinitialise l’exception et la méthode continue à s’exécuter. Elle échoue sur la nouvelle assertion. Pour résoudre le nouveau problème, nous ajoutons une instruction `return` après `StringAssert`. Le nouveau test confirme que nous avons résolu nos problèmes. Notre version finale de `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` ressemble à ce qui suit :  
  
```csharp  
[TestMethod]  
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()  
{  
    // arrange  
    double beginningBalance = 11.99;  
    double debitAmount = 20.0;  
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);  
  
    // act  
    try  
    {  
        account.Debit(debitAmount);  
    }  
    catch (ArgumentOutOfRangeException e)  
    {  
        // assert  
        StringAssert.Contains(e.Message, BankAccount. DebitAmountExceedsBalanceMessage);  
        return;  
    }  
    Assert.Fail("No exception was thrown.");  
}  
  
```  
  
 Dans cette section finale, le travail que nous avons fait en améliorant notre code de test a conduit à des méthodes de test plus fiables et plus instructives. Plus important encore, l’analyse supplémentaire a également abouti à une amélioration du code dans notre projet testé.
