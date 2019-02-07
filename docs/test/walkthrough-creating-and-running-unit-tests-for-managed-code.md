---
title: Créer et exécuter des tests unitaires pour le code managé
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
author: gewarren
ms.openlocfilehash: 12b232bf32be6802ccd82ecad647f2becc95addc
ms.sourcegitcommit: e3d96b20381916bf4772f9db52b22275763bb603
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484197"
---
# <a name="walkthrough-create-and-run-unit-tests-for-managed-code"></a>Procédure pas à pas : Créer et exécuter des tests unitaires pour le code managé

Cet article décrit la création, l’exécution et la personnalisation d’une série de tests unitaires à l’aide du framework de tests unitaires Microsoft pour le code managé et de **l’explorateur de tests** de Visual Studio. Vous commencez avec un projet C# qui est en développement, vous créez des tests qui utilisent son code, vous exécutez les tests et vous examinez les résultats. Ensuite, vous pouvez modifier le code de votre projet et réexécuter les tests.

> [!NOTE]
> Cette procédure pas à pas utilise le framework de tests unitaires Microsoft pour le code managé. **L’explorateur de tests** peut également exécuter des tests depuis des frameworks de tests unitaires tiers qui ont des adaptateurs pour **l’explorateur de tests**. Pour plus d’informations, consultez [Installer des frameworks de tests unitaires tiers](../test/install-third-party-unit-test-frameworks.md)

Pour plus d’informations sur la façon d’exécuter des tests à partir d’une ligne de commande, consultez [Options de ligne de commande VSTest.Console.exe](vstest-console-options.md).

## <a name="prerequisites"></a>Prérequis

- Le projet Bank. Consultez [Exemple de projet pour la création de tests unitaires](../test/sample-project-for-creating-unit-tests.md).

## <a name="create-a-project-to-test"></a>Créer un projet de test

1. Ouvrez Visual Studio.

2. Dans le menu **Fichier**, sélectionnez **Nouveau** > **Projet**.

   La boîte de dialogue **Nouveau projet** s’affiche.

3. Sous **Modèles installés**, cliquez sur **Visual C#**.

4. Dans la liste de types d’applications, cliquez sur **Bibliothèque de classes**.

5. Dans la zone **Nom**, tapez **Bank**, puis cliquez sur **OK**.

   Le nouveau projet Bank est créé et affiché dans **l’Explorateur de solutions**, avec le fichier *Class1.cs* ouvert dans l’éditeur de code.

   > [!NOTE]
   > Si *Class1.cs* n’est pas ouvert dans l’éditeur de code, double-cliquez sur le fichier *Class1.cs* dans l’**Explorateur de solutions** pour l’ouvrir.

6. Copiez le code source à partir de [l’Exemple de projet pour la création de tests unitaires](../test/sample-project-for-creating-unit-tests.md), puis remplacez le contenu d’origine de *Class1.cs* par le code copié.

7. Enregistrez le fichier avec le nom *BankAccount.cs*.

8. Dans le menu **Générer** , cliquez sur **Générer la solution**.

Vous avez maintenant un projet nommé Bank. Il contient le code source à tester et des outils avec lesquels le tester. L’espace de noms pour Bank, BankAccountNS, contient la classe publique BankAccount, dont vous testerez les méthodes dans les procédures suivantes.

Dans cet article, les tests se concentrent sur la méthode Debit. Cette méthode est appelée quand de l’argent est retiré d’un compte. Voici la définition de la méthode :

```csharp
// Method to be tested.
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

## <a name="create-a-unit-test-project"></a>Créer un projet de test unitaire

1. Dans le menu **Fichier**, sélectionnez **Ajouter** > **Nouveau projet**.

   > [!TIP]
   > Il existe deux autres façons d’ajouter un projet supplémentaire à une solution existante. Vous pouvez cliquer avec le bouton droit sur la solution dans l’**Explorateur de solutions**, puis choisir **Ajouter** > **Nouveau projet**. Vous pouvez aussi sélectionner **Fichier** > **Nouveau** > **Projet** puis, dans la boîte de dialogue **Nouveau projet**, sélectionnez l’option **Ajouter à la solution** :
   >
   > ![Option Ajouter à la solution dans la boîte de dialogue Nouveau projet](media/add-to-solution.png)

2. Dans la boîte de dialogue **Nouveau projet**, développez **Installé**, développez **Visual C#**, puis choisissez **Test**.

3. Dans la liste des modèles, sélectionnez **Projet de test unitaire**.

4. Dans la zone **Nom**, entrez `BankTests`, puis sélectionnez **OK**.

   Le projet **BankTests** est ajouté à la solution **Bank**.

5. Dans le projet **BankTests**, ajoutez une référence au projet **Bank**.

   Dans **l’Explorateur de solutions**, sélectionnez **Références** dans le projet **BankTests**, puis choisissez **Ajouter une référence** dans le menu contextuel (clic droit).

6. Dans la boîte de dialogue **Gestionnaire de références**, développez **Solution**, puis cochez l’élément **Bank**.

## <a name="create-the-test-class"></a>Créer la classe de test

Créez une classe de test pour vérifier la classe `BankAccount`. Vous pouvez utiliser le fichier *UnitTest1.cs* qui a été généré par le modèle de projet, mais donnez au fichier et à la classe des noms plus descriptifs. Vous pouvez effectuer cela en une seule étape en renommant le fichier dans **l’Explorateur de solutions**.

### <a name="rename-a-class-file"></a>Renommer un fichier de classe

Dans **l’Explorateur de solutions**, sélectionnez le fichier *UnitTest1.cs* dans le projet BankTests. Dans le menu contextuel (clic droit), choisissez **Renommer**, puis renommez le fichier *BankAccountTests.cs*. Choisissez **Oui** dans la boîte de dialogue qui vous demande si vous souhaitez renommer toutes les références à l’élément de code `UnitTest1` dans le projet.

Cette opération a pour effet de remplacer le nom de la classe par `BankAccountTests`. Le fichier *BankAccountTests.cs* contient maintenant le code suivant :

```csharp
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

### <a name="add-a-using-statement-to-the-project-under-test"></a>Ajouter une instruction using au projet testé

Vous pouvez également ajouter une instruction `using` à la classe pour pouvoir appeler le projet testé sans utiliser de noms complets. En haut du fichier de classe, ajoutez :

```csharp
using BankAccountNS;
```

### <a name="test-class-requirements"></a>Spécifications de la classe de test

Voici la configuration minimale requise pour une classe de test :

- L’attribut `[TestClass]` est requis dans le framework de tests unitaires Microsoft pour le code managé pour toute classe qui contient les méthodes de test unitaire à exécuter dans l’explorateur de tests.

- Chaque méthode de test à exécuter avec l’explorateur de tests doit avoir l’attribut `[TestMethod]`.

Vous pouvez avoir d’autres classes dans un projet de test unitaire qui n’ont pas l’attribut `[TestClass]` , et vous pouvez avoir d’autres méthodes dans les classes de test qui n’ont pas l’attribut `[TestMethod]` . Vous pouvez utiliser ces autres classes et méthodes dans vos méthodes de test.

## <a name="create-the-first-test-method"></a>Créer la première méthode de test

Dans cette procédure, vous écrivez des méthodes de test unitaire pour vérifier le comportement de la méthode `Debit` de la classe `BankAccount`. La méthode `Debit` est présentée plus haut dans cet article.

Il existe au moins trois comportements à vérifier :

- La méthode lève une exception <xref:System.ArgumentOutOfRangeException> si le montant du débit est supérieur au solde.

- La méthode lève <xref:System.ArgumentOutOfRangeException> si le montant du débit est inférieur à zéro.

- Si le montant du débit est valide, la méthode le soustrait du solde du compte.

> [!TIP]
> Vous pouvez supprimer la méthode `TestMethod1` par défaut, car vous ne l’utiliserez pas dans cette procédure pas à pas.

### <a name="to-create-a-test-method"></a>Pour créer une méthode de test

Le premier test vérifie qu’un montant valide (c’est-à-dire, inférieur au solde du compte et supérieur à zéro) retire le montant approprié du compte. Ajoutez la méthode suivante à cette classe `BankAccountTests` :

```csharp
[TestMethod]
public void Debit_WithValidAmount_UpdatesBalance()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 4.55;
    double expected = 7.44;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    account.Debit(debitAmount);

    // Assert
    double actual = account.Balance;
    Assert.AreEqual(expected, actual, 0.001, "Account not debited correctly");
}
```

La méthode est simple : elle met en place un nouvel objet `BankAccount` avec un solde de début, puis elle retire un montant valide. Elle utilise la méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A> pour vérifier que le solde de fin est conforme à ce qui est attendu.

### <a name="test-method-requirements"></a>Spécifications des méthodes de test

Une méthode de test doit répondre aux spécifications suivantes :

- Elle est décorée avec l’attribut `[TestMethod]`.

- Il retourne `void`.

- Elle ne peut pas avoir de paramètres.

## <a name="build-and-run-the-test"></a>Générer et exécuter le test

1. Dans le menu **Générer** , choisissez **Générer la solution**.

   En l’absence d’erreurs, **l’explorateur de tests** apparaît avec **Debit_WithValidAmount_UpdatesBalance** répertorié dans le groupe **Tests non exécutés**.

   > [!TIP]
   > Si **l’explorateur de tests** n’apparaît pas après une génération réussie, sélectionnez **Test** dans le menu, puis **Fenêtres**, puis **Explorateur de tests**.

2. Sélectionnez **Exécuter tout** pour exécuter le test. Pendant que le test s’exécute, la barre d’état en haut de la fenêtre s’anime. À l’issue de la série de tests, la barre devient verte si toutes les méthodes de test ont réussi, ou rouge si l’un des tests a échoué.

3. Dans ce cas, le test échoue. La méthode de test est déplacée vers le groupe **Échecs de tests**. Sélectionnez la méthode dans **l’explorateur de tests** pour en afficher les détails en bas de la fenêtre.

## <a name="fix-your-code-and-rerun-your-tests"></a>Vérifier votre code et exécuter à nouveau vos tests

### <a name="analyze-the-test-results"></a>Analyser les résultats des tests

Le résultat de test contient un message qui décrit l’échec. Pour la méthode `AreEqual`, le message affiche ce qui était attendu (le paramètre **Expected\<*valeur*>**) et ce qui a été reçu réellement (le paramètre **Actual\<*valeur*>**). Vous vous attendiez à ce que le solde diminue, mais il a augmenté du montant du retrait.

Le test unitaire a découvert un bogue : le montant du retrait est *ajouté* au solde du compte quand il doit être *soustrait*.

### <a name="correct-the-bug"></a>Corriger le bogue

Pour corriger l’erreur, remplacez la ligne :

```csharp
m_balance += amount;
```

Par :

```csharp
m_balance -= amount;
```

### <a name="rerun-the-test"></a>Réexécuter le test

Dans **l’Explorateur de tests**, choisissez **Exécuter tout** pour réexécuter le test. La barre rouge/verte devient verte pour indiquer que le test a réussi, puis le test est déplacé vers le groupe **Tests réussis**.

## <a name="use-unit-tests-to-improve-your-code"></a>Utiliser les tests unitaires pour améliorer votre code

Cette section décrit comment un processus itératif d’analyse, de développement de test unitaire et de refactorisation peut vous aider à rendre votre code de production plus fiable et efficace.

### <a name="analyze-the-issues"></a>Analyser les problèmes

Vous avez créé une méthode de test pour confirmer qu’un montant valide est correctement déduit dans la méthode `Debit`. À présent, vérifiez que la méthode lève une exception <xref:System.ArgumentOutOfRangeException> si le montant du débit est :

- supérieur au solde ou
- inférieur à zéro.

### <a name="create-the-test-methods"></a>Créer les méthodes de test

Créez une méthode de test pour vérifier que le comportement est correct quand le montant du débit est inférieur à zéro :

```csharp
[TestMethod]
[ExpectedException(typeof(ArgumentOutOfRangeException))]
public void Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = -100.00;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    account.Debit(debitAmount);

    // Assert is handled by the ExpectedException attribute on the test method.
}
```

Utilisez l’attribut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> pour déclarer que l’exception adéquate a été levée. L’attribut entraîne l’échec du test à moins qu’une exception <xref:System.ArgumentOutOfRangeException> ne soit levée. Si vous modifiez temporairement la méthode testée pour lever une <xref:System.ApplicationException> plus générique quand le montant du débit est inférieur à zéro, le test se comporte correctement&mdash;en l’occurrence, il échoue.

Pour tester le cas où le montant retiré est supérieur au solde, effectuez les étapes suivantes :

1. Créez une méthode de test nommée `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`.

2. Copiez le corps de la méthode depuis `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` vers la nouvelle méthode.

3. Définissez `debitAmount` sur un nombre supérieur au solde.

### <a name="run-the-tests"></a>Exécuter les tests

L’exécution des deux méthodes de test montre que les tests fonctionnent correctement.

### <a name="continue-the-analysis"></a>Poursuivre l’analyse

Toutefois, les deux dernières méthodes de test sont également troublantes. Vous ne pouvez pas savoir avec certitude quelle est la condition, dans la méthode testée, qui lève l’exception quand un des tests est exécuté. Si vous pouviez distinguer les deux conditions, c’est-à-dire, un montant de débit négatif ou un montant supérieur au solde, vous auriez davantage confiance dans les tests.

Examinez encore la méthode testée ; vous pouvez constater que les deux instructions conditionnelles utilisent un constructeur `ArgumentOutOfRangeException` qui accepte uniquement le nom de l’argument comme paramètre :

```csharp
throw new ArgumentOutOfRangeException("amount");
```

Vous pouvez utiliser un constructeur qui fournit des informations beaucoup plus riches : <xref:System.ArgumentOutOfRangeException.%23ctor(System.String,System.Object,System.String)> inclut le nom de l’argument, la valeur de l’argument et un message défini par l’utilisateur. Vous pouvez refactoriser la méthode testée pour utiliser ce constructeur. Encore mieux, vous pouvez utiliser les membres de type disponibles publiquement pour spécifier les erreurs.

### <a name="refactor-the-code-under-test"></a>Refactoriser le code testé

Tout d’abord, définissez deux constantes pour les messages d’erreur au niveau de la portée d’une classe. Placez-les dans la classe testée (BankAccount) :

```csharp
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";
public const string DebitAmountLessThanZeroMessage = "Debit amount is less than zero";
```

Ensuite, modifiez les deux instructions conditionnelles dans la méthode `Debit` :

```csharp
    if (amount > m_balance)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountExceedsBalanceMessage);
    }

    if (amount < 0)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountLessThanZeroMessage);
    }
```

### <a name="refactor-the-test-methods"></a>Refactoriser les méthodes de test

Supprimez l’attribut de méthode de test `ExpectedException` et, à la place, interceptez l’exception levée et vérifiez le message associé. La méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName> permet de comparer deux chaînes.

À présent, `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` peut se présenter comme suit :

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
    }
}
```

### <a name="retest-rewrite-and-reanalyze"></a>Retester, réécrire et réanalyser

Supposez qu’il y a un bogue dans la méthode testée et que la méthode `Debit` ne lève même pas d’exception <xref:System.ArgumentOutOfRangeException>, et ne génère pas non plus le bon message avec l’exception. Actuellement, la méthode de test ne gère pas ce cas. Si la valeur de `debitAmount` est valide (autrement dit, inférieure au solde mais supérieure à zéro), aucune exception n’est interceptée et l’assertion ne se déclenche donc jamais. Pourtant, la méthode de test réussit. Cela ne convient pas, car vous souhaitez que la méthode de test échoue si aucune exception n’est levée.

Il s’agit d’un bogue dans la méthode de test. Pour résoudre le problème, ajoutez une assertion <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> à la fin de la méthode de test pour gérer le cas où aucune exception n’est levée.

Cependant, une réexécution du test montre que le test *échoue* maintenant si l’exception correcte est interceptée. Le bloc `catch` intercepte l’exception, mais la méthode continue à s’exécuter et échoue au niveau de la nouvelle assertion <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A>. Pour résoudre ce problème, ajoutez une instruction `return` après `StringAssert` dans le bloc `catch`. La réexécution du test confirme que vous avez résolu ce problème. La version finale de `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` ressemble à ceci :

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
        return;
    }

    Assert.Fail("The expected exception was not thrown.");
}
```

Les améliorations apportées au code du test ont abouti à des méthodes de test plus robustes et plus informatives. Mais plus important encore, elles ont également amélioré le code testé.
