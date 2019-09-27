---
title: Concepts de base des tests unitaires
ms.date: 08/07/2019
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.CreateUnitTest
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aff50f5933d540297711e44487c775d93968f0fd
ms.sourcegitcommit: 689ba54ea14257d13031de881f5d4fe937a36f56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71342433"
---
# <a name="unit-test-basics"></a>Concepts de base des tests unitaires

Vérifiez que votre code fonctionne comme prévu en créant et en exécutant des tests unitaires. Un test unitaire consiste à décomposer les fonctionnalités de votre programme en comportements testables discrets que vous pouvez tester en tant qu’*unités* individuelles. L’explorateur de tests de Visual Studio offre un moyen souple et efficace d’exécuter vos tests unitaires et d’afficher leurs résultats dans Visual Studio. Visual Studio installe les infrastructures de tests unitaires Microsoft pour le code managé et le code natif. Utilisez une *infrastructure de tests unitaires* pour créer des tests unitaires, les exécuter et signaler les résultats de ces tests. Réexécutez des tests unitaires quand vous apportez des modifications pour vérifier que votre code fonctionne toujours correctement. Visual Studio Enterprise peut faire ceci automatiquement avec [Live Unit Testing](live-unit-testing-intro.md), qui détecte les tests affectés par les modifications de votre code et les exécute en arrière-plan au fil de votre frappe.

Les tests unitaires ont le plus d’effet sur la qualité du code quand ils font partie intégrante du flux de travail de votre développement logiciel. Dès que vous écrivez une fonction ou un autre bloc de code d’application, créez des tests unitaires pour vérifier le comportement du code en réponse aux cas standard, limite et incorrects des données d’entrée, ainsi que les hypothèses explicites ou implicites du code. Avec le *développement axé sur des tests*, comme vous créez les tests unitaires avant d’écrire le code, vous utilisez les tests unitaires comme documentation de conception et spécifications fonctionnelles.

Vous pouvez générer rapidement des projets de test et méthodes de test à partir de votre code, ou créer manuellement les tests quand vous le souhaitez. Quand vous utilisez IntelliTest pour explorer votre code .NET, vous pouvez générer des données de test et une suite de tests unitaires. Pour chaque instruction dans le code, une entrée de test est générée pour exécuter cette instruction. Découvrez comment [générer des tests unitaires pour votre code](generate-unit-tests-for-your-code-with-intellitest.md).

L’explorateur de tests peut également exécuter des infrastructures de tests unitaires tierces et open source ayant implémenté les interfaces des composants additionnels de l’explorateur de tests. Vous pouvez ajouter la plupart de ces frameworks dans le gestionnaire d’extensions de Visual Studio et la galerie Visual Studio. Pour plus d’informations, consultez [Installer des frameworks de tests unitaires de tiers](../test/install-third-party-unit-test-frameworks.md).

## <a name="get-started"></a>Prise en main

Pour obtenir une introduction aux tests unitaires qui vous conduit directement dans le code, consultez l’une des rubriques suivantes :

- [Procédure pas à pas : créer et exécuter des tests unitaires pour du code managé](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)

- [Démarrage rapide : développement piloté par les tests avec l’Explorateur de tests](../test/quick-start-test-driven-development-with-test-explorer.md)

- [Écrire des tests unitaires pour C/C++ dans Visual Studio](../test/writing-unit-tests-for-c-cpp.md)

## <a name="the-mybank-solution-example"></a>Exemple de solution MyBank

Dans cet article, nous utilisons comme exemple le développement d’une application fictive, appelée `MyBank`. Vous n’avez pas besoin du code réel pour suivre les explications fournies dans cette rubrique. Les méthodes de test sont écrites en C# et présentées à l’aide du framework de tests unitaires Microsoft pour le code managé. Toutefois, les concepts sont facilement transférés vers d’autres langages et frameworks.

::: moniker range="vs-2017"
![Solution MyBank](../test/media/ute_mybanksolution.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Solution MyBank 2019](../test/media/vs-2019/basics-mybank-solution.png)
::: moniker-end

Notre première tentative de conception de l’application `MyBank` inclut un composant Accounts (Comptes) qui représente un compte individuel et ses transactions avec la banque et un composant Database (Base de données) qui correspond à la fonction d’agrégation et de gestion des comptes individuels.

Nous créons une solution `MyBank` qui contient deux projets :

- `Accounts`

- `BankDb`

Notre première tentative de conception du projet `Accounts` comporte une classe destinée à détenir les informations de base d’un compte, une interface qui spécifie les fonctionnalités usuelles de n’importe quel type de compte, par exemple le dépôt ou le retrait d’argent sur le compte, ainsi qu’une classe dérivée de l’interface qui représente un compte courant. Nous commençons les projets Accounts (Comptes) en créant les fichiers sources suivants :

- *AccountInfo.cs* définit les informations de base d’un compte.

- *IAccount.cs* définit une interface `IAccount` standard pour un compte, y compris les méthodes pour déposer de l’argent sur un compte ou en retirer, et pour récupérer le solde du compte.

- *CheckingAccount.cs* contient la classe `CheckingAccount` qui implémente l’interface `IAccount` d’un compte courant.

Nous savons par expérience qu’un retrait sur un compte courant doit s’assurer que le montant retiré est inférieur au solde du compte. Aussi, nous remplaçons la méthode `IAccount.Withdraw` de `CheckingAccount` par une méthode qui vérifie cette condition. La méthode peut ressembler à ceci :

```csharp
public void Withdraw(double amount)
{
    if(m_balance >= amount)
    {
        m_balance -= amount;
    }
    else
    {
        throw new ArgumentException(nameof(amount), "Withdrawal exceeds balance!");
    }
}
```

Maintenant que nous avons le code, il est temps de le tester.

## <a name="create-unit-test-projects-and-test-methods"></a>Créer des projets de test unitaire et des méthodes de test

Il est souvent plus rapide de générer le projet de test unitaire et les stubs de test unitaire à partir de votre code. Vous pouvez également choisir de créer le projet de test unitaire et les tests manuellement selon vos besoins. Si vous voulez créer des tests unitaires avec un framework tiers, l’une de ces extensions doit être installée : [NUnit](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension-18371) ou [xUnit](https://marketplace.visualstudio.com/items?itemName=YowkoTsai.xUnitnetTestGenerator).

### <a name="generate-unit-test-project-and-unit-test-stubs"></a>Créer un projet de test unitaire et des stubs de test unitaire

1. Dans la fenêtre de l’éditeur de code, cliquez avec le bouton droit et choisissez [**Créer des tests unitaires**](create-unit-tests-menu.md) dans le menu contextuel.

   ::: moniker range="vs-2017"
   ![À partir de la fenêtre de l'éditeur, affichez le menu contextuel](../test/media/createunittestsrightclick.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![À partir de la fenêtre de l'éditeur, affichez le menu contextuel](../test/media/vs-2019/basics-create-unit-tests.png)
   ::: moniker-end

   > [!NOTE]
   > La commande de menu **Créer des tests unitaires** est uniquement disponible pour le code managé qui cible le .NET Framework (mais pas .NET Core).

2. Cliquez sur **OK** pour accepter les valeurs par défaut pour créer vos tests unitaires, ou changez les valeurs utilisées pour créer et nommer le projet de test unitaire et les tests unitaires. Vous pouvez sélectionner le code qui est ajouté par défaut aux méthodes de test unitaire.

   ![Boîte de dialogue Créer des tests unitaires dans Visual Studio](../test/media/create-unit-tests.png)

3. Les stubs de test unitaire sont créés dans un nouveau projet de test unitaire pour toutes les méthodes dans la classe.

   ::: moniker range="vs-2017"
   ![Les tests unitaires sont créés](../test/media/createunittestsstubs.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Les tests unitaires sont créés](../test/media/vs-2019/basics-test-stub.png)
   ::: moniker-end

4. Poursuivez votre lecture pour savoir comment [ajouter du code aux méthodes de test unitaire](#write-your-tests) et rendre votre test unitaire explicite, et des tests unitaires supplémentaires que vous pouvez ajouter pour tester votre code de manière approfondie.

### <a name="create-the-unit-test-project-and-unit-tests-manually"></a>Créer le projet de test unitaire et les tests unitaires manuellement

Un projet de test unitaire reflète généralement la structure d’un seul projet de code. Dans l’exemple MyBank, vous ajoutez deux projets de test unitaire nommés `AccountsTests` et `BankDbTests` à la solution `MyBanks` . Les noms des projets de test sont arbitraires, mais l’adoption d’une convention d’affectation de noms standard est une bonne idée.

**Pour ajouter un projet de test unitaire à une solution :**

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur la solution et choisissez **Ajouter** > **Nouveau** **Projet**.

::: moniker range="vs-2017"

2. Dans la boîte de dialogue **Nouveau projet**, développez le nœud **Installé**, choisissez le langage que vous voulez utiliser pour votre projet de test, puis sélectionnez **Test**.

3. Pour utiliser l’une des infrastructures de tests unitaires Microsoft, choisissez **Projet de test unitaire** dans la liste des modèles de projet. Sinon, choisissez le modèle de projet de l’infrastructure de tests unitaires que vous souhaitez utiliser. Pour tester le projet `Accounts` de notre exemple, vous devez le nommer `AccountsTests`.

   > [!NOTE]
   > Certaines infrastructures de tests unitaires tierces et open source ne fournissent pas de modèle de projet Visual Studio. Pour plus d’informations sur la création d’un projet, consultez la documentation relative à l’infrastructure.

::: moniker-end

::: moniker range=">=vs-2019"

2. Utilisez la zone de recherche de modèle de projet pour rechercher un modèle de projet de test unitaire pour le framework de test que vous voulez utiliser.

3. Dans la page suivante, nommez le projet. Pour tester le projet `Accounts` de notre exemple, vous pouvez le nommer `AccountsTests`.

::: moniker-end

4. Dans votre projet de test unitaire, ajoutez une référence au projet de code testé : le projet Accounts (Comptes) dans notre exemple.

   Pour créer la référence au projet de code :

   1. Sélectionnez le projet dans **l’Explorateur de solutions**.

   2. Dans le menu **Projet** , choisissez **Ajouter une référence**.

   3. Dans la boîte de dialogue **Gestionnaire de références**, ouvrez le nœud **Solution** et choisissez **Projets**. Sélectionnez le nom du projet de code et fermez la boîte de dialogue.

Chaque projet de test unitaire contient les classes qui reflètent les noms des classes du projet de code. Dans notre exemple, le projet `AccountsTests` contient les classes suivantes :

- la classe `AccountInfoTests` contient les méthodes de test unitaire pour la classe `AccountInfo` du projet `Accounts` ;

- la classe`CheckingAccountTests` contient les méthodes de test unitaire pour la classe `CheckingAccount` .

## <a name="write-your-tests"></a>Écrire vos tests

L’infrastructure de tests unitaires que vous utilisez et Visual Studio IntelliSense vous guident lors de l’écriture du code des tests unitaires pour un projet de code. Pour s’exécuter dans **l’explorateur de tests**, la plupart des infrastructures nécessitent que vous ajoutiez des attributs spécifiques pour identifier les méthodes de test unitaire. Les infrastructures fournissent également un moyen, généralement par le biais d’instructions assert ou d’attributs de méthode, pour indiquer si la méthode de test a réussi ou échoué. D’autres attributs identifient les méthodes facultatives d’installation lors de l’initialisation des classes et avant chaque méthode de test, ainsi que les méthodes de démontage qui sont exécutées après chaque méthode de test et avant la destruction de la classe.

Le modèle AAA (Arrange, Act, Assert) est un moyen couramment utilisé pour écrire les tests unitaires d’une méthode testée.

- La section **Arrange** d’une méthode de test unitaire initialise les objets et définit la valeur des données transmises à la méthode testée.

- La section **Act** appelle la méthode testée avec les paramètres triés.

- La section **Assert** vérifie que l’action de la méthode testée se comporte comme prévu.

Pour tester la méthode `CheckingAccount.Withdraw` de notre exemple, nous pouvons écrire deux tests : l’un qui vérifie le comportement standard de la méthode et l’autre qui vérifie qu’un retrait supérieur au solde échouera. Dans la classe `CheckingAccountTests` , nous ajoutons les méthodes suivantes :

```csharp
[TestMethod]
public void Withdraw_ValidAmount_ChangesBalance()
{
    // arrange
    double currentBalance = 10.0;
    double withdrawal = 1.0;
    double expected = 9.0;
    var account = new CheckingAccount("JohnDoe", currentBalance);

    // act
    account.Withdraw(withdrawal);

    // assert
    Assert.AreEqual(expected, account.Balance);
}

[TestMethod]
public void Withdraw_AmountMoreThanBalance_Throws()
{
    // arrange
    var account = new CheckingAccount("John Doe", 10.0);

    // act and assert
    Assert.ThrowsException<System.ArgumentException>(() => account.Withdraw(20.0));
}
```

Pour plus d’informations sur les infrastructures de tests unitaires Microsoft, consultez l’une des rubriques suivantes :

- [Tests unitaires sur votre code](unit-test-your-code.md)

- [Écriture de tests unitaires pour C/C++](writing-unit-tests-for-c-cpp.md)

- [Utiliser le framework MSTest dans les tests unitaires](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

## <a name="set-timeouts-for-unit-tests"></a>Définir des délais d’attente pour les tests unitaires

Si vous utilisez le framework MSTest, vous pouvez utiliser <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TimeoutAttribute> pour définir un délai d’attente sur une méthode de test individuelle :

```csharp
[TestMethod]
[Timeout(2000)]  // Milliseconds
public void My_Test()
{ ...
}
```

Pour affecter au délai d’attente la valeur maximale autorisée :

```csharp
[TestMethod]
[Timeout(TestTimeout.Infinite)]  // Milliseconds
public void My_Test ()
{ ...
}
```

## <a name="run-tests-in-test-explorer"></a>Exécuter des tests dans l’explorateur de tests

Quand vous générez le projet de test, les tests s’affichent dans **l’explorateur de tests**. Si **l’explorateur de tests** n’est pas visible, sélectionnez **Test** dans le menu Visual Studio et choisissez **Fenêtres**, puis **Explorateur de tests**.

::: moniker range="vs-2017"
![Explorateur de tests unitaires](../test/media/ute_failedpassednotrunsummary.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Explorateur de tests unitaires](../test/media/vs-2019/basics-test-explorer.png)
::: moniker-end

À mesure que vous exécutez, écrivez et réexécutez vos tests, l’**Explorateur de tests** peut afficher les résultats dans les groupes **Échecs de tests**, **Tests réussis**, **Tests ignorés** et **Tests non exécutés**. Différentes options de regroupement sont disponibles dans la barre d’outils.

Vous pouvez également filtrer les tests de n’importe quelle vue sur le texte de la zone de recherche au niveau global ou en sélectionnant l’un des filtres prédéfinis. Vous pouvez exécuter une sélection des tests à tout moment. Les résultats d’une série de tests sont immédiatement visibles dans la barre réussite/échec en haut de la fenêtre de l’explorateur. Les détails d’un résultat de méthode de test sont affichés quand vous sélectionnez le test.

### <a name="run-and-view-tests"></a>Exécuter et afficher des tests

La barre d’outils de **l’explorateur de tests** vous permet de découvrir, d’organiser et d’exécuter les tests qui vous intéressent.

::: moniker range="vs-2017"
![Exécuter des tests à partir de la barre d'outils de l'explorateur de tests](../test/media/ute_toolbar.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Exécuter des tests à partir de la barre d'outils de l'explorateur de tests](../test/media/vs-2019/test-explorer-toolbar-diagram-16-2.png)
::: moniker-end

Vous pouvez choisir **Exécuter tout** pour exécuter tous vos tests ou **Exécuter** pour sélectionner un sous-ensemble de tests à exécuter. Sélectionnez un test pour en afficher les spécificités dans le volet de détails. Choisissez **Ouvrir le test** dans le menu contextuel (clic droit) (clavier : **F12**) pour afficher le code source du test sélectionné.

::: moniker range="vs-2017"

Si les tests individuels n’ont aucune dépendance qui les empêche d’être exécutés dans n’importe quel ordre, activez l’exécution parallèle des tests avec le bouton bascule ![UTE&#95;parallelicon&#45;small](../test/media/ute_parallelicon-small.png) dans la barre d’outils. Cela peut réduire sensiblement le temps nécessaire pour exécuter tous les tests.

::: moniker-end

::: moniker range=">=vs-2019"

Si les tests individuels n’ont aucune dépendance qui les empêche d’être exécutés dans n’importe quel ordre, activez l’exécution parallèle des tests dans le menu Paramètres de la barre d’outils. Cela peut réduire sensiblement le temps nécessaire pour exécuter tous les tests.

::: moniker-end

### <a name="run-tests-after-every-build"></a>Exécuter des tests après chaque génération

::: moniker range="vs-2017"

|Bouton|Description|
|-|-|
|![Exécuter après les builds](../test/media/ute_runafterbuild_btn.png)|Pour exécuter vos tests unitaires après chaque génération locale, choisissez **Test** dans le menu standard, puis **Exécuter les tests après la génération** dans la barre d’outils de **l’Explorateur de tests**.|

> [!NOTE]
> L’exécution de tests unitaires après chaque génération nécessite Visual Studio 2017 édition Enterprise ou Visual Studio 2019. Dans Visual Studio 2019, la fonctionnalité est disponible dans les éditions Enterprise, Community et Professional.

::: moniker-end

::: moniker range=">=vs-2019"

Pour exécuter vos tests unitaires après chaque build locale, ouvrez l’icône des paramètres dans la barre d’outils de l’Explorateur de tests, puis sélectionnez **Exécuter les tests après la build**.

::: moniker-end

### <a name="filter-and-group-the-test-list"></a>Regrouper et filtrer la liste de tests

Quand vous avez un grand nombre de tests, vous pouvez taper du texte dans la zone de recherche de l’**Explorateur de tests** pour filtrer la liste selon la chaîne spécifiée. Vous pouvez limiter votre filtre encore plus en choisissant parmi la liste des filtres.

::: moniker range="vs-2017"
![Rechercher des catégories de filtre](../test/media/ute_searchfilter.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Rechercher des catégories de filtre](../test/media/vs-2019/test-explorer-search-filter-16-2.png)
::: moniker-end

|Bouton|Description|
|-|-|
|![Bouton du groupe d'explorateur de tests](../test/media/ute_groupby_btn.png)|Pour regrouper vos tests par catégorie, choisissez le bouton **Grouper par** .|

Pour plus d’informations, consultez [Exécuter des tests unitaires avec l’Explorateur de tests](../test/run-unit-tests-with-test-explorer.md).

## <a name="qa"></a>Questions et réponses

**Q : Comment déboguer des tests unitaires ?**

**R :** Utilisez l’**Explorateur de tests** pour démarrer une session de débogage de vos tests. L’exécution pas à pas de votre code avec le débogueur Visual Studio vous conduit de manière transparente à des allers et retours entre les tests unitaires et le projet testé. Pour démarrer le débogage :

1. Dans l’éditeur Visual Studio, définissez un point d’arrêt dans une ou plusieurs méthodes de test que vous souhaitez déboguer.

    > [!NOTE]
    > Comme les méthodes de test peuvent s'exécuter dans n'importe quel ordre, définissez les points d'arrêt dans toutes les méthodes de test que vous souhaitez déboguer.

2. Dans **l’explorateur de tests**, sélectionnez les méthodes de test, puis choisissez **Déboguer les tests sélectionnés** dans le menu contextuel.

En savoir plus sur le [débogage des tests unitaires](../debugger/debugger-feature-tour.md).

**Q : Si j’utilise le TDD (développement piloté par les tests), comment générer du code à partir de mes tests ?**

**R :** Utilisez Actions rapides pour générer des classes et des méthodes dans votre code de projet. Écrivez une instruction dans une méthode de test qui appelle la classe ou la méthode que vous souhaitez générer, puis ouvrez l’ampoule qui apparaît sous l’erreur. Si l’appel concerne un constructeur de la nouvelle classe, choisissez **Générer le type** dans le menu et suivez l’Assistant pour insérer la classe dans votre projet de code. Si l’appel concerne une méthode, choisissez **Générer la méthode** à partir du menu IntelliSense.

::: moniker range="vs-2017"
![Menu de l’action rapide Générer un stub de méthode](../test/media/ute_generatemethodstubintellisense.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Menu de l’action rapide Générer un stub de méthode](../test/media/vs-2019/basics-generate-method-tdd.png)
::: moniker-end

**Q : Puis-je créer des tests unitaires qui acceptent plusieurs ensembles de données en entrée pour exécuter le test ?**

**R :** Oui. Les*méthodes de test pilotées par les données* vous permettent de tester une plage de valeurs avec une méthode de test unitaire unique. Utilisez un attribut `DataSource` pour la méthode de test qui spécifie la source de données et la table contenant les valeurs des variables que vous voulez tester.  Dans le corps de la méthode, vous affectez les valeurs de ligne aux variables à l’aide de l’indexeur `TestContext.DataRow[`*ColumnName*`]` .

> [!NOTE]
> Ces procédures s’appliquent uniquement aux méthodes de test que vous écrivez à l’aide de l’infrastructure de tests unitaires Microsoft pour le code managé. Si vous utilisez un autre framework, consultez sa documentation pour obtenir des fonctionnalités équivalentes.

Par exemple, supposons que nous ajoutions une méthode superflue à la classe `CheckingAccount` nommée `AddIntegerHelper`. `AddIntegerHelper` ajoute deux entiers.

Pour créer un test piloté par les données pour la méthode `AddIntegerHelper`, nous créons d’abord une base de données Access intitulée *AccountsTest.accdb* et une table nommée `AddIntegerHelperData`. La table `AddIntegerHelperData` définit les colonnes pour spécifier les premier et deuxième opérandes de l’addition, et une colonne pour spécifier le résultat attendu. Nous remplissons un certain nombre de lignes avec les valeurs appropriées.

```csharp
[DataSource(
    @"Provider=Microsoft.ACE.OLEDB.12.0;Data Source=C:\Projects\MyBank\TestData\AccountsTest.accdb",
    "AddIntegerHelperData"
)]
[TestMethod()]
public void AddIntegerHelper_DataDrivenValues_AllShouldPass()
{
    var target = new CheckingAccount();
    int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);
    int y = Convert.ToInt32(TestContext.DataRow["SecondNumber"]);
    int expected = Convert.ToInt32(TestContext.DataRow["Sum"]);
    int actual = target.AddIntegerHelper(x, y);
    Assert.AreEqual(expected, actual);
}
```

La méthode attribuée s’exécute une fois pour chaque ligne de la table. **L’explorateur de tests** indique un échec du test de la méthode si l’une des itérations échoue. Le volet Détails des résultats du test de la méthode vous indique le statut réussite/échec pour chaque ligne de données.

En savoir plus sur les [tests unitaires pilotés par les données](../test/how-to-create-a-data-driven-unit-test.md).

**Q : Puis-je voir la quantité de code testée par mes tests unitaires ?**

**R :** Oui. Vous pouvez déterminer la quantité de code qui est réellement testée par vos tests unitaires à l’aide de l’outil de couverture du code Visual Studio dans Visual Studio Enterprise. Les langages natifs et managés ainsi que toutes les infrastructures de tests unitaires qui peuvent être exécutés par l’infrastructure de tests unitaires sont pris en charge.

Vous pouvez exécuter la couverture de code sur les tests sélectionnés ou sur tous les tests d’une solution. La fenêtre **Résultats de la couverture du code** affiche le pourcentage des blocs du code du produit qui ont été testés par ligne, fonction, classe, espace de noms et module.

Pour exécuter la couverture du code pour les méthodes de test dans une solution, choisissez **test** > **analyser la couverture du code pour tous les tests**.

Les résultats de la couverture apparaissent dans la fenêtre **Résultats de la couverture du code**.

![Résultats de la couverture du code](../test/media/ute_codecoverageresults.png)

En savoir plus sur la [couverture du code](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) .

**Q : Puis-je tester des méthodes de mon code qui ont des dépendances externes ?**

**R :** Oui. Si vous disposez de Visual Studio Enterprise, Microsoft Fakes peut être utilisé avec les méthodes de test que vous écrivez à l’aide des infrastructures de tests unitaires pour le code managé.

Microsoft Fakes utilise deux approches pour créer des classes de substitution pour les dépendances externes :

1. Les*stubs* génèrent des classes de substitution dérivées de l’interface parente de la classe de dépendance cible. Les méthodes stub peuvent être remplacées par des méthodes virtuelles publiques de la classe cible.

2. Les*shims* utilisent l’instrumentation du runtime pour rediriger les appels à une méthode cible vers une méthode shim de substitution pour les méthodes non virtuelles.

Dans les deux approches, vous utilisez les délégués générés des appels à la méthode de dépendance pour spécifier le comportement souhaité dans la méthode de test.

En savoir plus sur l’ [isolement des méthodes de test unitaire avec Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).

**Q : Puis-je utiliser d’autres frameworks de tests unitaires pour créer des tests unitaires ?**

**R :** Oui, suivez ces étapes pour [rechercher et installer d’autres frameworks](../test/install-third-party-unit-test-frameworks.md). Après le redémarrage de Visual Studio, rouvrez votre solution pour créer vos tests unitaires, puis sélectionnez vos infrastructures installées ici :

![Sélectionner un autre framework de test unitaire installé](../test/media/createunittestsdialogextensions.png)

Vos stubs de test unitaire seront créés à l’aide de l’infrastructure sélectionnée.
