---
title: Bien démarrer avec les tests unitaires
description: Utilisez Visual Studio pour définir et exécuter des tests unitaires afin de maintenir l’intégrité du code et rechercher les erreurs et les erreurs avant les clients.
ms.custom: SEO-VS-2020
ms.date: 04/07/2020
ms.topic: tutorial
helpviewer_keywords:
- unit testing, create unit test plans
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c83b13b852b9ae53bd2218a62b6681478369df1b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970515"
---
# <a name="get-started-with-unit-testing"></a>Bien démarrer avec les tests unitaires

Utilisez Visual Studio pour définir et exécuter des tests unitaires afin de maintenir l’intégrité du code, garantir la couverture du code, et rechercher les erreurs et les défauts avant que vos clients les trouvent. Exécutez vos tests unitaires fréquemment pour vérifier que votre code fonctionne correctement.

Dans cet article, le code et les illustrations utilisent C#, mais les concepts et les fonctionnalités s’appliquent aux langages .NET, C++, Python, JavaScript et la machine à écrire.

## <a name="create-unit-tests"></a>Créer des tests unitaires

Cette section décrit comment créer un projet de test unitaire.

1. Ouvrez le projet que vous souhaitez tester dans Visual Studio.

   Dans le cadre de la démonstration d’un exemple de test unitaire, cet article teste un projet C# simple « Hello World » nommé **HelloWorldCore**. L’exemple de code pour un tel projet est comme suit :

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

1. Dans l’**Explorateur de solutions**, sélectionnez le nœud de la solution. Puis, dans la barre de menus supérieure, sélectionnez **fichier**  >  **Ajouter**  >  **un nouveau projet**.

1. Dans la boîte de dialogue Nouveau projet, recherchez un modèle de projet de test unitaire pour l’infrastructure de test que vous souhaitez utiliser, par exemple MSTest, puis sélectionnez-le.

   À compter de Visual Studio 2017 version 14,8, les langages .NET incluent des modèles intégrés pour NUnit et xUnit. Pour C++, vous devrez sélectionner une infrastructure de test prise en charge par le langage. Pour Python, consultez [configurer des tests unitaires dans le code python](../python/unit-testing-python-in-visual-studio.md) pour configurer votre projet de test.

   > [!TIP]
   > Pour C#, vous pouvez créer des projets de test unitaire à partir du code à l’aide d’une méthode plus rapide. Pour plus d’informations, consultez [créer des projets de test unitaire et des méthodes de test](../test/unit-test-basics.md#create-unit-test-projects-and-test-methods). Pour utiliser cette méthode avec .NET Core ou .NET Standard, Visual Studio 2019 est requis.

   L’illustration suivante montre un test unitaire MSTest qui est pris en charge dans .NET.

   ::: moniker range=">=vs-2019"

   ![Modèle de projet de test unitaire dans Visual Studio 2019](media/vs-2019/add-new-test-project.png)

   Cliquez sur **Suivant**, choisissez un nom pour le projet de test, puis cliquez sur **Créer**.

   ::: moniker-end

   ::: moniker range="vs-2017"

   ![Modèle de projet de test unitaire dans Visual Studio 2019](media/mstest-test-project-template.png)

   Choisissez un nom pour le projet de test, par exemple HelloWorldTests, puis cliquez sur **OK**.

   ::: moniker-end

   Le projet est ajouté à votre solution.

   ![Projet de test unitaire dans l’Explorateur de solutions](media/vs-2019/solution-explorer.png)

1. Dans le projet de test unitaire, ajoutez une référence au projet que vous voulez tester. Pour ce faire, cliquez avec le bouton droit sur **Références** ou **Dépendances**, puis choisissez **Ajouter une référence**.

1. Sélectionnez le projet qui contient le code que vous allez tester, puis cliquez sur **OK**.

   ![Ajouter une référence de projet dans Visual Studio](media/vs-2019/reference-manager.png)

1. Ajoutez du code à la méthode de test unitaire.

   Par exemple, vous pouvez utiliser le code suivant en sélectionnant l’onglet de documentation approprié qui correspond à votre infrastructure de test : MSTest, NUnit ou xUnit (pris en charge sur .NET uniquement).

   # <a name="mstest"></a>[MSTest](#tab/mstest)

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

   # <a name="nunit"></a>[NUnit](#tab/nunit)

   ```csharp
   using NUnit.Framework;
   using System.IO;
   using System;

   namespace HelloWorldTests
   {
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

    # <a name="xunit"></a>[xUnit](#tab/xunit)

    ```csharp
    using System;
    using Xunit;
    using System.IO;
    
    namespace HelloWorldTests
    {
        public class UnitTest1
        {
            private const string Expected = "Hello World!";
            [Fact]
            public void Test1()
            {
                using (var sw = new StringWriter())
                {
                    Console.SetOut(sw);
                    HelloWorldCore.Program.Main();
    
                    var result = sw.ToString().Trim();
                    Assert.Equal(Expected, result);
                }
            }
        }
    }
    ```

## <a name="run-unit-tests"></a>Exécuter des tests unitaires

1. Ouvrez l' [Explorateur de tests](../test/run-unit-tests-with-test-explorer.md).

   ::: moniker range=">=vs-2019"
   Pour ouvrir l’Explorateur de tests, sélectionnez **tester** > l' **Explorateur de tests** dans la barre de menus supérieure (ou appuyez sur **CTRL** + **E**, **T**).
   ::: moniker-end
   ::: moniker range="vs-2017"
   Pour ouvrir l’Explorateur de tests, choisissez **tester** >  > l' **Explorateur de tests** Windows dans la barre de menus supérieure.
   ::: moniker-end

1. Exécutez vos tests unitaires en cliquant sur **exécuter tout** (ou appuyez sur **CTRL**  +  **R**, **V**).

   ![Exécuter des tests unitaires dans l'Explorateur de tests](media/vs-2019/test-explorer-run-all.png)

   Une fois les tests terminés, une coche verte indique qu’un test a réussi. Une icône « x » rouge indique qu’un test a échoué.

   ![Examiner les résultats des tests unitaires dans l’Explorateur de tests](media/vs-2019/unit-test-passed.png)

> [!TIP]
> Vous pouvez utiliser l’[Explorateur de tests](../test/run-unit-tests-with-test-explorer.md) pour exécuter des tests unitaires à partir du framework de tests intégré (MSTest) ou à partir de frameworks de tests tiers. Vous pouvez regrouper les tests en catégories, filtrer la liste de tests, ainsi que créer, enregistrer et exécuter des sélections de tests. Vous pouvez également déboguer des tests et analyser les performances des tests et la couverture du code.

## <a name="view-live-unit-test-results-visual-studio-enterprise"></a>Afficher les résultats des tests unitaires en direct (Visual Studio Enterprise)

Si vous utilisez le framework de tests MSTest, xUnit ou NUnit dans Visual Studio 2017 ou une version ultérieure, vous pouvez afficher les résultats temps réel de vos tests unitaires.

> [!NOTE]
> Pour suivre ces étapes, Visual Studio Enterprise est requis.

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

## <a name="use-a-third-party-test-framework"></a>Utiliser un framework de tests tiers

Vous pouvez exécuter des tests unitaires dans Visual Studio à l’aide d’infrastructures de test tierces telles que Boost, Google et NUnit, en fonction de votre langage de programmation. Pour utiliser un Framework tiers :

- Utilisez le **Gestionnaire de package NuGet** pour installer le package NuGet pour le framework de votre choix.

- ASP.net À compter de Visual Studio 2017 version 14,6, Visual Studio comprend des modèles de projet de test préconfigurés pour les infrastructures de test NUnit et xUnit. Les modèles incluent également les packages NuGet nécessaires pour activer la prise en charge.

- C++ Dans Visual Studio 2017 et versions ultérieures, certaines infrastructures comme Boost sont déjà incluses. Pour plus d’informations, consultez [écrire des tests unitaires pour C/C++ dans Visual Studio](../test/writing-unit-tests-for-c-cpp.md).

Pour ajouter un projet de test unitaire :

1. Ouvrez la solution qui contient le code à tester.

2. Cliquez avec le bouton droit sur la solution dans l’**Explorateur de solutions**, puis choisissez **Ajouter** > **Nouveau projet**.

3. Sélectionnez un modèle de projet de test unitaire.

   Dans cet exemple, sélectionnez [nunit](https://nunit.org/) .

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

6. Exécutez le test à partir de l' **Explorateur de tests** ou en cliquant avec le bouton droit sur le code de test et en choisissant **exécuter les tests** (ou **CTRL**  +  **R**, **T**).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Concepts de base des tests unitaires](../test/unit-test-basics.md)

> [!div class="nextstepaction"]
> [Créer et exécuter des tests unitaires pour le code managé](walkthrough-creating-and-running-unit-tests-for-managed-code.md)
