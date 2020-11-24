---
title: Tests unitaires C# – Tutoriel
description: Découvrez comment créer, exécuter et personnaliser une série de tests unitaires à l’aide de l’infrastructure de tests unitaires Microsoft pour le code managé et l’Explorateur de tests de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 05/14/2019
ms.topic: conceptual
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
author: mikejo5000
ms.openlocfilehash: ed2e7f11a6e36c797bb6c506c19b0fff11fb5ad1
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95598547"
---
# <a name="walkthrough-create-and-run-unit-tests-for-managed-code"></a>Procédure pas à pas : Créer et exécuter des tests unitaires pour le code managé

Cet article décrit la création, l’exécution et la personnalisation d’une série de tests unitaires à l’aide du framework de tests unitaires Microsoft pour le code managé et de **l’explorateur de tests** de Visual Studio. Vous commencez avec un projet C# qui est en développement, vous créez des tests qui utilisent son code, vous exécutez les tests et vous examinez les résultats. Vous modifiez ensuite le code de projet et réexécutez les tests.



## <a name="create-a-project-to-test"></a>Créer un projet de test

::: moniker range="vs-2017"

1. Ouvrez Visual Studio.

2. Dans le menu **fichier** , sélectionnez **nouveau** > **projet**.

   La boîte de dialogue **Nouveau projet** apparaît.

3. Sous la catégorie **Visual C#** > **.NET Core**, choisissez le modèle de projet **Application console (.NET Core)**.

4. Nommez le projet **Bank**, puis cliquez sur **OK**.

   Le projet Bank est créé et affiché dans l’**Explorateur de solutions**, avec le fichier *Program.cs* ouvert dans l’éditeur de code.

   > [!NOTE]
   > Si *Program.cs* n’est pas ouvert dans l’éditeur, double-cliquez sur le fichier *Program.cs* dans l’**Explorateur de solutions** pour l’ouvrir.

::: moniker-end

::: moniker range=">=vs-2019"

1. Ouvrez Visual Studio.

2. Dans la fenêtre Démarrer, choisissez **créer un nouveau projet**.

3. Recherchez et sélectionnez le modèle de projet **Application console (.NET Core)** C#, puis cliquez sur **Suivant**.

4. Nommez le projet **Bank**, puis cliquez sur **Créer**.

   Le projet Bank est créé et affiché dans l’**Explorateur de solutions**, avec le fichier *Program.cs* ouvert dans l’éditeur de code.

   > [!NOTE]
   > Si *Program.cs* n’est pas ouvert dans l’éditeur, double-cliquez sur le fichier *Program.cs* dans l’**Explorateur de solutions** pour l’ouvrir.

::: moniker-end

5. Remplacez le contenu de *Program.cs* par le code C# suivant qui définit une classe, *BankAccount* :

   ```csharp
   using System;

   namespace BankAccountNS
   {
       /// <summary>
       /// Bank account demo class.
       /// </summary>
       public class BankAccount
       {
           private readonly string m_customerName;
           private double m_balance;

           private BankAccount() { }

           public BankAccount(string customerName, double balance)
           {
               m_customerName = customerName;
               m_balance = balance;
           }

           public string CustomerName
           {
               get { return m_customerName; }
           }

           public double Balance
           {
               get { return m_balance; }
           }

           public void Debit(double amount)
           {
               if (amount > m_balance)
               {
                   throw new ArgumentOutOfRangeException("amount");
               }

               if (amount < 0)
               {
                   throw new ArgumentOutOfRangeException("amount");
               }

               m_balance += amount; // intentionally incorrect code
           }

           public void Credit(double amount)
           {
               if (amount < 0)
               {
                   throw new ArgumentOutOfRangeException("amount");
               }

               m_balance += amount;
           }

           public static void Main()
           {
               BankAccount ba = new BankAccount("Mr. Bryan Walton", 11.99);

               ba.Credit(5.77);
               ba.Debit(11.22);
               Console.WriteLine("Current balance is ${0}", ba.Balance);
           }
       }
   }
   ```

6. Renommez le fichier *BankAccount.cs* en effectuant un clic droit et en choisissant **Renommer** dans l’**Explorateur de solutions**.

7. Dans le menu **Générer**, cliquez sur **Générer la solution**.

Vous disposez maintenant d’un projet avec des méthodes que vous pouvez tester. Dans cet article, les tests se limitent à la méthode `Debit`. La méthode `Debit` est appelée quand de l’argent est retiré sur un compte.

## <a name="create-a-unit-test-project"></a>Créer un projet de test unitaire

1. Dans le menu **Fichier**, sélectionnez **Ajouter** > **Nouveau projet**.

   > [!TIP]
   > Vous pouvez aussi cliquer avec le bouton droit sur la solution dans l’**Explorateur de solutions**, puis choisir **Ajouter** > **Nouveau projet**.

::: moniker range="vs-2017"

2. Dans la boîte de dialogue **nouveau projet** , développez **installé**, développez **Visual C#**, puis choisissez **test**.

3. Dans la liste des modèles, sélectionnez **Projet de test MSTest (.NET Core)**.

4. Dans la zone **Nom**, entrez `BankTests`, puis sélectionnez **OK**.

   Le projet **BankTests** est ajouté à la solution **Bank**.

::: moniker-end

::: moniker range=">=vs-2019"

2. Recherchez et sélectionnez le modèle de projet **Projet de test MSTest (.NET Core)** C#, puis cliquez sur **Suivant**.

3. Nommez le projet **BankTests**.

4. Cliquez sur **Créer**.

   Le projet **BankTests** est ajouté à la solution **Bank**.

::: moniker-end

5. Dans le projet **BankTests**, ajoutez une référence au projet **Bank**.

   Dans l’**Explorateur de solutions**, sélectionnez **Dépendances** sous le projet **BankTests**, puis choisissez **Ajouter une référence** dans le menu contextuel (clic droit).

6. Dans la boîte de dialogue **Gestionnaire de références**, développez **Projets**, sélectionnez **Solution**, puis cochez l’élément **Bank**.

7. Choisissez **OK**.

## <a name="create-the-test-class"></a>Créer la classe de test

Créez une classe de test pour vérifier la classe `BankAccount`. Vous pouvez utiliser le fichier *UnitTest1.cs* qui a été généré par le modèle de projet, mais donnez au fichier et à la classe des noms plus descriptifs.

### <a name="rename-a-file-and-class"></a>Renommer un fichier et une classe

1. Pour renommer le fichier, dans l’**Explorateur de solutions**, sélectionnez le fichier *UnitTest1.cs* dans le projet BankTests. Dans le menu contextuel (clic droit), choisissez **Renommer**, puis renommez le fichier *BankAccountTests.cs*.

::: moniker range="vs-2017"

2. Pour renommer la classe, choisissez **Oui** dans la boîte de dialogue qui s’affiche et vous demande si vous voulez aussi renommer les références à l’élément de code.

::: moniker-end

::: moniker range=">=vs-2019"

2. Pour renommer la classe, positionnez le curseur sur `UnitTest1` dans l’éditeur de code, cliquez avec le bouton droit, puis choisissez **Renommer**. Tapez **BankAccountTests**, puis appuyez sur **Entrée**.

::: moniker-end

Le fichier *BankAccountTests.cs* contient maintenant le code suivant :

```csharp
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

### <a name="add-a-using-statement"></a>Ajoutez une instruction using

Ajoutez une [ `using` instruction](/dotnet/csharp/language-reference/keywords/using-statement) à la classe de test pour pouvoir appeler le projet testé sans utiliser de noms qualifiés complets. En haut du fichier de classe, ajoutez :

```csharp
using BankAccountNS;
```

### <a name="test-class-requirements"></a>Spécifications de la classe de test

Voici la configuration minimale requise pour une classe de test :

- L’attribut `[TestClass]` est obligatoire sur une classe qui contient les méthodes de test unitaire à exécuter dans l’Explorateur de tests.

- Chaque méthode de test que l’Explorateur de tests doit reconnaître doit avoir l’attribut `[TestMethod]`.

Vous pouvez avoir d’autres classes dans un projet de test unitaire qui n’ont pas l’attribut `[TestClass]` , et vous pouvez avoir d’autres méthodes dans les classes de test qui n’ont pas l’attribut `[TestMethod]` . Vous pouvez appeler ces autres classes et méthodes à partir de vos méthodes de test.

## <a name="create-the-first-test-method"></a>Créer la première méthode de test

Dans cette procédure, vous écrivez des méthodes de test unitaire pour vérifier le comportement de la méthode `Debit` de la classe `BankAccount`.

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

La méthode est simple : elle met en place un nouvel objet `BankAccount` avec un solde de début, puis retire un montant valide. Elle utilise la méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=nameWithType> pour vérifier que le solde de fin est conforme à ce qui est attendu.

### <a name="test-method-requirements"></a>Spécifications des méthodes de test

Une méthode de test doit répondre aux spécifications suivantes :

- Elle est décorée avec l’attribut `[TestMethod]`.

- Elle retourne `void`.

- Elle ne peut pas avoir de paramètres.

## <a name="build-and-run-the-test"></a>Générer et exécuter le test

1. Dans le menu **Générer** , choisissez **Générer la solution**.

2. Si l’**Explorateur de tests** n’est pas ouvert, ouvrez-le en choisissant **Test** > **Fenêtres** > **Explorateur de tests** à partir de la barre de menus supérieure.

3. Sélectionnez **Exécuter tout** pour exécuter le test.

   Pendant que le test s’exécute, la barre d’état en haut de la fenêtre **Explorateur de tests** s’anime. À l’issue de la série de tests, la barre devient verte si toutes les méthodes de test ont réussi, ou rouge si l’un des tests a échoué.

   Dans ce cas, le test échoue.

4. Sélectionnez la méthode dans l' **Explorateur de tests** pour afficher les détails en bas de la fenêtre.

## <a name="fix-your-code-and-rerun-your-tests"></a>Vérifier votre code et exécuter à nouveau vos tests

Le résultat de test contient un message qui décrit l’échec. Pour la méthode `AreEqual`, le message affiche ce qui était attendu et ce qui a été réellement reçu. Vous vous attendiez à ce que le solde diminue, mais il a augmenté du montant du retrait.

Le test unitaire a découvert un bogue : le montant du retrait est *ajouté* au solde du compte quand il doit être *soustrait*.

### <a name="correct-the-bug"></a>Corriger le bogue

Pour corriger l’erreur, dans le fichier *BankAccount.cs*, remplacez la ligne :

```csharp
m_balance += amount;
```

par :

```csharp
m_balance -= amount;
```

### <a name="rerun-the-test"></a>Réexécuter le test

Dans l' **Explorateur de tests**, choisissez **exécuter tout** pour réexécuter le test. La barre rouge/verte devient verte pour indiquer que le test a réussi.

![Explorateur de tests dans Visual Studio 2019 indiquant la réussite du test](media/test-explorer-banktests-passed.png)

## <a name="use-unit-tests-to-improve-your-code"></a>Utiliser les tests unitaires pour améliorer votre code

Cette section décrit comment un processus itératif d’analyse, de développement de test unitaire et de refactorisation peut vous aider à rendre votre code de production plus fiable et efficace.

### <a name="analyze-the-issues"></a>Analyser les problèmes

Vous avez créé une méthode de test pour confirmer qu’un montant valide est correctement déduit dans la méthode `Debit`. À présent, vérifiez que la méthode lève une exception <xref:System.ArgumentOutOfRangeException> si le montant du débit est :

- supérieur au solde ou
- inférieur à zéro.

### <a name="create-and-run-new-test-methods"></a>Créer et exécuter de nouvelles méthodes de test

Créez une méthode de test pour vérifier que le comportement est correct quand le montant du débit est inférieur à zéro :

```csharp
[TestMethod]
public void Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = -100.00;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act and assert
    Assert.ThrowsException<System.ArgumentOutOfRangeException>(() => account.Debit(debitAmount));
}
```

Utilisez la méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> pour déclarer que l’exception adéquate a été levée. Cette méthode entraîne l’échec du test, à moins qu’une exception <xref:System.ArgumentOutOfRangeException> ne soit levée. Si vous modifiez temporairement la méthode testée pour lever une <xref:System.ApplicationException> plus générique quand le montant du débit est inférieur à zéro, le test se comporte correctement&mdash;en l’occurrence, il échoue.

Pour tester le cas où le montant retiré est supérieur au solde, effectuez les étapes suivantes :

1. Créez une méthode de test nommée `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`.

2. Copiez le corps de la méthode depuis `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` vers la nouvelle méthode.

3. Définissez `debitAmount` sur un nombre supérieur au solde.

Exécutez les deux tests et vérifiez qu’ils réussissent.

### <a name="continue-the-analysis"></a>Poursuivre l’analyse

La méthode en cours de test peut être améliorée. Avec l’implémentation actuelle, nous n’avons aucun moyen de savoir quelle condition (`amount > m_balance` ou `amount < 0`) a conduit à l’exception levée pendant le test. Nous savons simplement qu’un `ArgumentOutOfRangeException` a été généré quelque part dans la méthode. Il serait préférable de pouvoir dire quelle condition dans `BankAccount.Debit` a provoqué l’exception levée (`amount > m_balance` ou `amount < 0`) afin d’être convaincu que notre méthode effectue certaines vérifications des arguments correctement et en toute sécurité.

Examinez à nouveau la méthode testée (`BankAccount.Debit`) et constatez que les deux instructions conditionnelles utilisent un constructeur `ArgumentOutOfRangeException` qui accepte uniquement le nom de l’argument comme paramètre :

```csharp
throw new ArgumentOutOfRangeException("amount");
```

Vous pouvez utiliser un constructeur qui fournit des informations beaucoup plus riches : <xref:System.ArgumentOutOfRangeException.%23ctor(System.String,System.Object,System.String)> inclut le nom de l’argument, la valeur de l’argument et un message défini par l’utilisateur. Vous pouvez refactoriser la méthode testée pour utiliser ce constructeur. Encore mieux, vous pouvez utiliser les membres de type disponibles publiquement pour spécifier les erreurs.

### <a name="refactor-the-code-under-test"></a>Refactoriser le code testé

Tout d’abord, définissez deux constantes pour les messages d’erreur au niveau de la portée d’une classe. Placez-les dans la classe testée (`BankAccount`) :

```csharp
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";
public const string DebitAmountLessThanZeroMessage = "Debit amount is less than zero";
```

Ensuite, modifiez les deux instructions conditionnelles dans la méthode `Debit` :

```csharp
if (amount > m_balance)
{
    throw new System.ArgumentOutOfRangeException("amount", amount, DebitAmountExceedsBalanceMessage);
}

if (amount < 0)
{
    throw new System.ArgumentOutOfRangeException("amount", amount, DebitAmountLessThanZeroMessage);
}
```

### <a name="refactor-the-test-methods"></a>Refactoriser les méthodes de test

Refactorisez les méthodes de test en supprimant l’appel à <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType>. Placez l’appel à `Debit()` dans un bloc `try/catch`, interceptez l’exception spécifique qui est attendue et vérifiez le message associé. La méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName> permet de comparer deux chaînes.

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
    catch (System.ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
    }
}
```

### <a name="retest-rewrite-and-reanalyze"></a>Retester, réécrire et réanalyser

Actuellement, la méthode de test ne gère pas tous les cas qu’elle devrait. Si la méthode testée, la `Debit` méthode, n’a pas réussi à lever une <xref:System.ArgumentOutOfRangeException> lorsque la valeur `debitAmount` était supérieure au solde (ou inférieure à zéro), la méthode de test passerait. Cela ne convient pas, car vous souhaitez que la méthode de test échoue si aucune exception n’est levée.

Il s’agit d’un bogue dans la méthode de test. Pour résoudre le problème, ajoutez une assertion <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> à la fin de la méthode de test pour gérer le cas où aucune exception n’est levée.

La réexécution du test montre que le test *échoue* maintenant si l’exception correcte est interceptée. Le bloc `catch` intercepte l’exception, mais la méthode continue à s’exécuter et échoue au niveau de la nouvelle assertion <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A>. Pour résoudre ce problème, ajoutez une instruction `return` après `StringAssert` dans le bloc `catch`. La réexécution du test confirme que vous avez résolu ce problème. La version finale de `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` ressemble à ceci :

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
    catch (System.ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
        return;
    }

    Assert.Fail("The expected exception was not thrown.");
}
```

### <a name="conclusion"></a>Conclusion

Les améliorations apportées au code du test ont abouti à des méthodes de test plus robustes et plus informatives. Mais plus important encore, elles ont également amélioré le code testé.

> [!TIP]
> Cette procédure pas à pas utilise le framework de tests unitaires Microsoft pour le code managé. L’**Explorateur de tests** peut aussi exécuter des tests à partir de frameworks de tests unitaires tiers qui ont des adaptateurs pour l’**Explorateur de tests**. Pour plus d’informations, consultez [Installer des frameworks de tests unitaires de tiers](../test/install-third-party-unit-test-frameworks.md).

## <a name="see-also"></a>Voir aussi

Pour plus d’informations sur la façon d’exécuter des tests à partir d’une ligne de commande, consultez [Options de ligne de commande VSTest.Console.exe](vstest-console-options.md).
