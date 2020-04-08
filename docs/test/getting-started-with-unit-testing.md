---
title: Bien démarrer avec les tests unitaires
ms.date: 04/07/2020
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit test plans
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d961af66658d6924da1b5ba38b9ec7f2a8b19aaa
ms.sourcegitcommit: c3b6af7367bef67a02c37404534229b935f713a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80892790"
---
# <a name="get-started-with-unit-testing"></a>Bien démarrer avec les tests unitaires

Utilisez Visual Studio pour définir et exécuter des tests unitaires afin de maintenir l’intégrité du code, garantir la couverture du code, et rechercher les erreurs et les défauts avant que vos clients les trouvent. Exécutez vos tests unitaires fréquemment pour vérifier que votre code fonctionne correctement.

## <a name="create-unit-tests"></a>Créer des tests unitaires

Cette section décrit comment créer un projet d’essai unitaire.

1. Ouvrez le projet que vous souhaitez tester dans Visual Studio.

   Pour démontrer un test d’unité d’exemple, cet article teste un simple projet "Hello World" nommé **HelloWorldCore**. L’exemple de code pour un tel projet est comme suit :

   ```csharp
   namespace HelloWorldCore

      public class Program
      {
         public static void Main()
         {
            Console.WriteLine("Hello World!");
         }
      }
   ```

1. Dans l’**Explorateur de solutions**, sélectionnez le nœud de la solution. Ensuite, à partir de la barre de menu haut, sélectionnez **File** > **Ajouter** > **nouveau projet**.

1. Dans la boîte de dialogue Nouveau projet, recherchez un modèle de projet de test unitaire pour le framework de test que vous voulez utiliser, puis sélectionnez-le.

   ::: moniker range=">=vs-2019"

   ![Modèle de projet de test unitaire dans Visual Studio 2019](media/vs-2019/add-new-test-project.png)

   Cliquez sur **Suivant**, choisissez un nom pour le projet de test, puis cliquez sur **Créer**.

   ::: moniker-end

   ::: moniker range="vs-2017"

   ![Modèle de projet de test unitaire dans Visual Studio 2019](media/mstest-test-project-template.png)

   Choisissez un nom pour le projet de test, puis cliquez sur **OK**.

   ::: moniker-end

   Le projet est ajouté à votre solution.

   ![Projet de test unitaire dans l’Explorateur de solutions](media/vs-2019/solution-explorer.png)

1. Dans le projet de test unitaire, ajoutez une référence au projet que vous voulez tester. Pour ce faire, cliquez avec le bouton droit sur **Références** ou **Dépendances**, puis choisissez **Ajouter une référence**.

1. Sélectionnez le projet qui contient le code que vous allez tester, puis cliquez sur **OK**.

   ![Ajouter une référence de projet dans Visual Studio](media/vs-2019/reference-manager.png)

1. Ajoutez du code à la méthode de test unitaire.

   Par exemple, pour un projet MSTest, vous pouvez utiliser le code suivant.

   ```csharp
   using Microsoft.VisualStudio.TestTools.UnitTesting;
   using System.IO;
   using System;

   namespace HelloWorldTests
   {
      [TestClass]
      public class UnitTest1
      {
         private const string Expected = "Hello World!";
         [TestMethod]
         public void TestMethod1()
         {
            using (var sw = new StringWriter())
            {
               Console.SetOut(sw);
               HelloWorldCore.Program.Main();

               var result = sw.ToString().Trim();
               Assert.AreEqual(Expected, result);
            }
         }
      }
   }
   ```

   Ou, pour un projet NUnit, vous pouvez utiliser le code suivant.

   ```csharp
   using using NUnit.Framework;
   using System.IO;
   using System;

   namespace HelloWorldTests
   {
      [TestClass]
      public class Tests
      {
         private const string Expected = "Hello World!";

         [SetUp]
         public void Setup()
         {
         }
         [Test]
         public void TestMethod1()
         {
            using (var sw = new StringWriter())
            {
               Console.SetOut(sw);
               HelloWorldCore.Program.Main();

               var result = sw.ToString().Trim();
               Assert.AreEqual(Expected, result);
            }
         }
      }
   }
   ```

> [!TIP]
> Pour plus de détails sur la création de tests unitaires, voir [Créer et exécuter des tests unitaires pour le code géré](walkthrough-creating-and-running-unit-tests-for-managed-code.md).

## <a name="run-unit-tests"></a>Exécuter des tests unitaires

1. Open [Test Explorer](../test/run-unit-tests-with-test-explorer.md).

   ::: moniker range=">=vs-2019"
   Pour ouvrir Test Explorer, choisissez **Test** > **Explorer** dans la barre de menu du haut.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Pour ouvrir Test Explorer, choisissez **Test** > **Windows** > **Test Explorer** à partir de la barre de menu supérieure.
   ::: moniker-end

1. Exécutez vos tests unitaires en cliquant sur **Tout exécuter**.

   ![Exécuter des tests unitaires dans l'Explorateur de tests](media/vs-2019/test-explorer-run-all.png)

   Une fois les tests terminés, une coche verte indique qu’un test a réussi. Une icône « x » rouge indique qu’un test a échoué.

   ![Examiner les résultats des tests unitaires dans l’Explorateur de tests](media/vs-2019/unit-test-passed.png)

> [!TIP]
> Vous pouvez utiliser l’[Explorateur de tests](../test/run-unit-tests-with-test-explorer.md) pour exécuter des tests unitaires à partir du framework de tests intégré (MSTest) ou à partir de frameworks de tests tiers. Vous pouvez regrouper les tests en catégories, filtrer la liste de tests, ainsi que créer, enregistrer et exécuter des sélections de tests. Vous pouvez également déboguer des tests et analyser les performances des tests et la couverture du code.

## <a name="view-live-unit-test-results"></a>Afficher les résultats des tests unitaires en direct

Si vous utilisez le framework de tests MSTest, xUnit ou NUnit dans Visual Studio 2017 ou une version ultérieure, vous pouvez afficher les résultats temps réel de vos tests unitaires.

> [!NOTE]
> Live Unit Testing est disponible uniquement dans la version Enterprise.

1. Activez les tests unitaires en direct à partir du menu **Test** en choisissant **Test** > **Live Unit Testing** > **Démarrer**.

   ::: moniker range="vs-2017"

   ![Activer les tests unitaires en direct](media/live-test-results-start.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Démarrer les tests unitaires en direct dans Visual Studio 2019](media/vs-2019/start-live-unit-testing.png)

   ::: moniker-end

1. Affichez les résultats des tests dans la fenêtre d’éditeur de code quand vous écrivez et modifiez le code.

   ![Afficher les résultats des tests](media/vs-2019/live-unit-testing-results.png)

1. Cliquez sur un indicateur de résultat de test pour afficher plus d’informations, comme les noms des tests qui couvrent cette méthode.

   ![Choisir les indicateurs des résultats des tests](media/vs-2019/live-unit-testing-details.png)

Pour plus d’informations sur les tests unitaires en direct, consultez [Tests unitaires en direct](../test/live-unit-testing-intro.md).

## <a name="generate-unit-tests-with-intellitest"></a>Générer des tests unitaires avec IntelliTest

Quand vous exécutez IntelliTest, vous pouvez identifier les tests qui échouent et ajouter le code nécessaire pour les corriger. Vous pouvez sélectionner les tests générés à enregistrer dans un projet de test pour fournir une suite de régression. À mesure que vous modifiez votre code, relancez IntelliTest pour synchroniser les tests générés avec les changements de code. Pour savoir comment procéder, voir [Générer des tests unitaires de code avec IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).

> [!TIP]
> IntelliTest est disponible uniquement pour le code managé qui cible le .NET Framework.

![Génération de tests unitaires avec IntelliTest](media/intellitest.png)

## <a name="analyze-code-coverage"></a>Analyser la couverture du code

Pour déterminer la proportion de code de votre projet qui sera réellement testée par des tests codés, par exemple des tests unitaires, recourez à la fonctionnalité de couverture du code de Visual Studio. Pour assurer une protection efficace contre les bogues, les tests doivent porter sur une part importante du code. Pour savoir comment, consultez [la couverture du code pour déterminer la quantité de code testée.](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)

## <a name="use-a-third-party-test-framework"></a>Utiliser un framework de tests tiers

Vous pouvez exécuter des tests unitaires dans Visual Studio à l’aide de frameworks de tests tiers tels que Boost, Google et NUnit. Utilisez le **Gestionnaire de package NuGet** pour installer le package NuGet pour le framework de votre choix. Ou, pour les frameworks de tests NUnit et xUnit, Visual Studio inclut des modèles de projets de test préconfigurés qui incluent les packages NuGet nécessaires.

Pour créer des tests unitaires qui utilisent [NUnit](https://nunit.org/) :

1. Ouvrez la solution qui contient le code à tester.

2. Cliquez avec le bouton droit sur la solution dans l’**Explorateur de solutions**, puis choisissez **Ajouter** > **Nouveau projet**.

3. Sélectionnez le modèle de projet **Projet de test NUnit**.

   ::: moniker range=">=vs-2019"

   ![Modèle de projet de test NUnit dans Visual Studio 2019](media/vs-2019/nunit-test-project-template.png)

   Cliquez sur **Suivant**, nommez le projet, puis cliquez sur **Créer**.

   ::: moniker-end

   ::: moniker range="vs-2017"

   Nommez le projet, puis cliquez sur **OK** pour le créer.

   ::: moniker-end

   Le modèle de projet inclut des références NuGet à NUnit et NUnit3TestAdapter.

   ![Dépendances NuGet de NUnit dans l’Explorateur de solutions](media/vs-2019/nunit-nuget-dependencies.png)

4. Ajoutez une référence du projet de test au projet qui contient le code à tester.

   Cliquez avec le bouton droit sur le projet dans **l’Explorateur de solutions**, puis sélectionnez **Ajouter** > **Référence**. (Vous pouvez également ajouter une référence à partir du menu contextuel du nœud **Références** ou **Dépendances**.)

5. Ajoutez du code à votre méthode de test.

   ![Ajouter du code à votre fichier de code de test unitaire](media/vs-2019/unit-test-method.png)

6. Exécutez le test à partir de l’**Explorateur de tests**, ou en cliquant avec le bouton droit sur le code de test et en choisissant **Exécuter les tests**.

## <a name="see-also"></a>Voir aussi

* [Procédure pas à pas : Créer et exécuter des tests unitaires pour le code managé](walkthrough-creating-and-running-unit-tests-for-managed-code.md)
* [Créer des tests unitaires, commande](create-unit-tests-menu.md)
* [Générer des tests avec IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [Exécuter des tests avec l’Explorateur de tests](run-unit-tests-with-test-explorer.md)
* [Analyser la couverture du code](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
