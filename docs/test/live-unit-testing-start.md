---
title: Découvrir comment tester votre code avec Live Unit Test 2017
description: Apprenez à utiliser Live Unit Testing en créant une bibliothèque de classes simple qui cible .NET Standard et en créant un projet MSTest qui cible .NET Core pour le tester.
ms.custom: SEO-VS-2020
ms.date: 04/03/2020
ms.topic: how-to
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 2270216e7245f20d26df580ad90dc627319adcc1
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798633"
---
# <a name="get-started-with-live-unit-testing"></a>Bien démarrer avec Live Unit Testing

Quand vous activez Live Unit Testing dans une solution Visual Studio, cela représente visuellement la couverture des tests et l’état de vos tests. Live Unit Testing exécute également dynamiquement des tests chaque fois que vous modifiez votre code et vous avertit immédiatement lorsque vos modifications provoquent l’échec des tests.

Live Unit Testing peut être utilisé pour tester des solutions qui ciblent .NET Framework ou .NET Core. Dans ce didacticiel, vous allez apprendre à utiliser Live Unit Testing en créant une bibliothèque de classes simple qui cible .NET Standard, et vous créerez un projet MSTest qui cible .NET Core pour le tester.

La solution C# complète peut être téléchargée à partir du dépôt GitHub [MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/).

## <a name="prerequisites"></a>Prérequis

Ce didacticiel nécessite que vous ayez installé Visual Studio Enterprise Edition avec la charge de travail de **développement multiplateforme .net Core** .

## <a name="create-the-solution-and-the-class-library-project"></a>Créer la solution et le projet de bibliothèque de classes

Commencez par créer une solution Visual Studio nommée UtilityLibraries qui se compose d’un seul projet de bibliothèque de classes .NET Standard, StringLibrary.

La solution est simplement un conteneur pour un ou plusieurs projets. Pour créer une solution vide, ouvrez Visual Studio et effectuez les étapes suivantes :

1. Sélectionnez **fichier**  >  **nouveau**  >  **projet** dans le menu Visual Studio de niveau supérieur.

1. Tapez **solution** dans la zone de recherche des modèles, puis sélectionnez le modèle **Solution vide**. Nommez le projet **UtilityLibraries**.

   ::: moniker range="vs-2017"

   ![Boîte de dialogue **Nouveau projet**](./media/lut-start/new-solution.png)

   ::: moniker-end

1. Terminez la création de la solution.

Maintenant que vous avez créé la solution, vous allez créer une bibliothèque de classes nommée StringLibrary qui contient un certain nombre de méthodes d’extension pour l’utilisation de chaînes.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur la solution UtilityLibraries et sélectionnez **Ajouter**  >  **nouveau projet**.

::: moniker range="vs-2017"

2. Dans la boîte de dialogue **Ajouter un nouveau projet**, sélectionnez le nœud C#, puis sélectionnez **.NET Standard**.

   > [!NOTE]
   > Étant donné que notre bibliothèque cible .NET Standard plutôt qu’une implémentation .NET particulière, elle peut être appelée à partir de n’importe quelle implémentation .NET qui prend en charge cette version de .NET Standard. Pour plus d'informations, consultez [.NET Standard](/dotnet/standard/net-standard).

3. Sélectionnez le modèle **bibliothèque de classes (.NET standard)** dans le volet droit, puis entrez **StringLibrary** dans la zone de texte **nom** , comme le montre l’illustration suivante :

   ![Boîte de dialogue **Ajouter un nouveau projet**](./media/lut-start/add-project-cs.png)

4. Sélectionnez **OK** pour créer le projet.

::: moniker-end

::: moniker range=">=vs-2019"

2. Tapez **bibliothèque de classes** dans la zone de recherche des modèles, puis sélectionnez le modèle **Bibliothèque de classes (.NET Standard)**. Cliquez sur **Suivant**.

   > [!NOTE]
   > Étant donné que notre bibliothèque cible .NET Standard plutôt qu’une implémentation .NET particulière, elle peut être appelée à partir de n’importe quelle implémentation .NET qui prend en charge cette version de .NET Standard. Pour plus d'informations, consultez [.NET Standard](/dotnet/standard/net-standard).

3. Nommez le projet **StringLibrary**.

4. Cliquez sur **Créer** pour créer le projet.

::: moniker-end

5. Remplacez tout le code existant dans l’éditeur de code par le code suivant :

   ```csharp
   using System;

   namespace UtilityLibraries
   {
       public static class StringLibrary
       {
           public static bool StartsWithUpper(this string s)
           {
               if (String.IsNullOrWhiteSpace(s))
                   return false;

               return Char.IsUpper(s[0]);
           }

           public static bool StartsWithLower(this string s)
           {
               if (String.IsNullOrWhiteSpace(s))
                   return false;

               return Char.IsLower(s[0]);
           }

           public static bool HasEmbeddedSpaces(this string s)
           {
               foreach (var ch in s.Trim())
               {
                   if (ch == ' ')
                       return true;
               }
               return false;
           }
       }
   }
   ```

   StringLibrary a trois méthodes statiques :

   - `StartsWithUpper` retourne `true` si une chaîne commence par un caractère majuscule ; sinon, elle retourne `false`.

   - `StartsWithLower` retourne `true` si une chaîne commence par un caractère minuscule ; sinon, elle retourne `false`.

   - `HasEmbeddedSpaces` retourne `true` si une chaîne contient un espace incorporé ; sinon, elle retourne `false`.

6. Sélectionnez **générer**  >  **générer la solution** dans le menu Visual Studio de niveau supérieur. La génération doit s’effectuer correctement.

## <a name="create-the-test-project"></a>Créer le projet de test

L’étape suivante consiste à créer le projet de test unitaire pour tester la bibliothèque StringLibrary. Créez les tests unitaires en procédant comme suit :

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur la solution UtilityLibraries et sélectionnez **Ajouter**  >  **nouveau projet**.

::: moniker range="vs-2017"

2. Dans la boîte de dialogue **Ajouter un nouveau projet**, sélectionnez le nœud C#, puis sélectionnez **.NET Core**.

   > [!NOTE]
   > Vous ne devez pas nécessairement écrire vos tests unitaires dans le même langage que celui de votre bibliothèque de classes.

3. Sélectionnez le modèle **projet de test unitaire (.net Core)** dans le volet droit, puis entrez **StringLibraryTests** dans la zone de texte **nom** , comme le montre l’illustration suivante :

   ![Boîte de dialogue **Ajouter un nouveau projet** pour le projet de test unitaire](./media/lut-start/add-unit-test-cs.png)

4. Sélectionnez **OK** pour créer le projet.

   > [!NOTE]
   > Ce didacticiel de démarrage utilise Live Unit Testing avec le framework de test MSTest. Vous pouvez également utiliser les frameworks de test xUnit et NUnit.

::: moniker-end

::: moniker range=">=vs-2019"

2. Tapez **test unitaire** dans la zone de recherche de modèle, sélectionnez **C#** comme langage, puis sélectionnez le **projet de test unitaire** pour le modèle .net core. Cliquez sur **Suivant**.

   > [!NOTE]
   > À compter de Visual Studio 2019 version 16,9, le nom du modèle de projet MSTest est passé du **projet de test unitaire MSTest (.net Core)** au **projet de test unitaire**.

3. Nommez le projet **StringLibraryTests** , puis cliquez sur **suivant**.

4. Choisissez le Framework cible recommandé (.NET Core 3,1) ou .NET 5, puis choisissez **créer**.

   > [!NOTE]
   > Ce didacticiel de démarrage utilise Live Unit Testing avec le framework de test MSTest. Vous pouvez également utiliser les frameworks de test xUnit et NUnit.

::: moniker-end

5. Le projet de test unitaire ne peut pas accéder automatiquement à la bibliothèque de classes qu’il teste. Vous donnez l’accès à la bibliothèque test en ajoutant une référence au projet de bibliothèque de classes. Pour ce faire, cliquez avec le bouton droit sur le `StringLibraryTests` projet et sélectionnez **Ajouter** une  >  **référence**. Dans la boîte de dialogue **Gestionnaire de références** , vérifiez que l’onglet **solution** est sélectionné, puis sélectionnez le projet StringLibrary, comme indiqué dans l’illustration suivante.

   ![Boîte de dialogue **Gestionnaire de références**](./media/lut-start/add-reference.png)

6. Remplacez le code de test unitaire réutilisable fourni par le modèle par le code suivant :

   ```csharp
   using System;
   using Microsoft.VisualStudio.TestTools.UnitTesting;
   using UtilityLibraries;

   namespace StringLibraryTest
   {
       [TestClass]
       public class UnitTest1
       {
           [TestMethod]
           public void TestStartsWithUpper()
           {
               // Tests that we expect to return true.
               string[] words = { "Alphabet", "Zebra", "ABC", "Αθήνα", "Москва" };
               foreach (var word in words)
               {
                   bool result = word.StartsWithUpper();
                   Assert.IsTrue(result,
                                 $"Expected for '{word}': true; Actual: {result}");
               }
           }

           [TestMethod]
           public void TestDoesNotStartWithUpper()
           {
               // Tests that we expect to return false.
               string[] words = { "alphabet", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                                  "1234", ".", ";", " " };
               foreach (var word in words)
               {
                   bool result = word.StartsWithUpper();
                   Assert.IsFalse(result,
                                  $"Expected for '{word}': false; Actual: {result}");
               }
           }

           [TestMethod]
           public void DirectCallWithNullOrEmpty()
           {
               // Tests that we expect to return false.
               string[] words = { String.Empty, null };
               foreach (var word in words)
               {
                   bool result = StringLibrary.StartsWithUpper(word);
                   Assert.IsFalse(result,
                                  $"Expected for '{(word == null ? "<null>" : word)}': " +
                                  $"false; Actual: {result}");
               }
           }
       }
   }
   ```

7. Enregistrez votre projet en sélectionnant l’icône **Enregistrer** dans la barre d’outils.

   Étant donné que le code de test unitaire comprend des caractères non-ASCII, la boîte de dialogue suivante s’affiche pour vous avertir que certains caractères seront perdus si vous enregistrez le fichier dans son format ASCII par défaut.

8. Choisissez le bouton **Enregistrer avec un autre encodage**.

   ![Choisir un encodage de fichier](media/lut-start/ascii-encoding.png)

9. Dans la liste déroulante **encodage** de la boîte de dialogue **options d’enregistrement avancées** , choisissez **Unicode (UTF-8 sans signature)-CodePage 65001**, comme le montre l’illustration suivante :

   ![Choix de l’encodage UTF-8](media/lut-start/utf8-encoding.png)

10. Compilez le projet de test unitaire en sélectionnant **générer** la  >  **solution reconstruire** dans le menu Visual Studio de niveau supérieur.

Vous avez créé une bibliothèque de classes, ainsi que quelques tests unitaires pour celle-ci. Vous avez maintenant terminé les préliminaires nécessaires pour utiliser Live Unit Testing.

## <a name="enable-live-unit-testing"></a>Activer Live Unit Testing

Jusqu’à présent, bien que vous ayez écrit les tests de la bibliothèque de classes StringLibrary, vous ne les avez pas exécutés. Live Unit Testing les exécute automatiquement une fois que vous l’activez. Pour cela, procédez comme suit :

1. Si vous le souhaitez, sélectionnez la fenêtre de l’éditeur de code qui contient le code pour StringLibrary. Il s’agit de *Class1. cs* pour un projet C# ou *Class1. vb* pour un projet Visual Basic. (Cette étape vous permet d’inspecter visuellement le résultat de vos tests et l’étendue de la couverture du code une fois que vous avez activé Live Unit Testing.)

1. Sélectionnez **test**  >  **Live Unit testing**  >  **Démarrer** dans le menu Visual Studio de niveau supérieur.

1. Visual Studio démarre Live Unit Test, qui exécute automatiquement tous vos tests.

::: moniker range="vs-2017"
Quand il a terminé l’exécution de vos tests, **l’Explorateur de tests** affiche les résultats globaux et les résultats des tests individuels. En outre, la fenêtre de l’éditeur de code affiche graphiquement la couverture de votre code de test et le résultat de vos tests. Comme le montre l’illustration suivante, les trois tests ont été exécutés avec succès. Elle montre également que nos tests ont couvert tous les chemins de code de la méthode `StartsWithUpper`, et que ces tests ont tous été exécutés avec succès (ce qui est indiqué par la coche verte, « ✓ »). Enfin, elle montre qu’aucune des autres méthodes de StringLibrary n’a de couverture du code (qui est indiquée par une ligne bleue, « ➖ »).

![Fenêtre Explorateur de tests et éditeur de code après le démarrage de Live Unit testing](media/lut-start/lut-results-cs.png)
::: moniker-end
::: moniker range=">=vs-2019"
Une fois l’exécution de vos tests terminée, **Live Unit testing** affiche à la fois les résultats globaux et le résultat des tests individuels. En outre, la fenêtre de l’éditeur de code affiche graphiquement la couverture de votre code de test et le résultat de vos tests. Comme le montre l’illustration suivante, les trois tests ont été exécutés avec succès. Elle montre également que nos tests ont couvert tous les chemins de code de la méthode `StartsWithUpper`, et que ces tests ont tous été exécutés avec succès (ce qui est indiqué par la coche verte, « ✓ »). Enfin, elle montre qu’aucune des autres méthodes de StringLibrary n’a de couverture du code (qui est indiquée par une ligne bleue, « ➖ »).

![L’Explorateur de tests en direct et la fenêtre de l’éditeur de code après le démarrage de Live Unit testing](media/lut-start/vs-2019/lut-results-cs.png)
::: moniker-end

Vous pouvez également obtenir des informations plus détaillées sur la couverture des tests et les résultats des tests en sélectionnant une icône de couverture du code particulière dans la fenêtre de l’éditeur de code. Pour examiner ces informations détaillées, procédez comme suit :

1. Cliquez sur la marque de coche verte pour la ligne qui contient `if (String.IsNullOrWhiteSpace(s))` dans la méthode `StartsWithUpper`. Comme le montre l’illustration suivante, Live Unit Testing indique que trois tests couvrent cette ligne de code, et que tous ont été exécutés avec succès.

   ![Couverture du code pour l’instruction conditionnelle « if »](media/lut-start/code-coverage-cs1.png)

1. Cliquez sur la marque de coche verte pour la ligne qui contient `return Char.IsUpper(s[0])` dans la méthode `StartsWithUpper`. Comme le montre l’illustration suivante, Live Unit Testing indique que seuls deux tests couvrent cette ligne de code, et que tous ont été exécutés avec succès.

   ![Couverture du code pour l’instruction return](media/lut-start/code-coverage-cs2.png)

Le principal problème identifié par Live Unit Testing est une couverture du code incomplète. Vous le résolvez dans la section suivante.

## <a name="expand-test-coverage"></a>Étendre la couverture des tests

Dans cette section, vous étendez vos tests unitaires à la méthode `StartsWithLower`. Quand vous faites cela, Live Unit Testing continue à tester dynamiquement votre code.

Pour étendre la couverture du code à la méthode `StartsWithLower`, procédez comme suit :

1. Ajoutez les méthodes `TestStartsWithLower` et `TestDoesNotStartWithLower` au fichier de code source de test de votre projet :

   :::code language="csharp" source="../test/samples/snippets/csharp/lut-start/unittest2.cs" id="Snippet1":::

1. Modifiez la `DirectCallWithNullOrEmpty` méthode en ajoutant le code suivant immédiatement après l’appel à la [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) méthode.

   :::code language="csharp" source="../test/samples/snippets/csharp/lut-start/unittest2.cs" id="Snippet2":::

1. Live Unit Testing exécute automatiquement des tests nouveaux et modifiés quand vous modifiez votre code source. Comme le montre l’illustration suivante, tous les tests, y compris ceux que vous avez ajoutés et ceux que vous avez modifiés, ont réussi.

   ::: moniker range="vs-2017"
   ![Explorateur de tests après avoir développé la couverture de test](media/lut-start/test-dynamic.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![L’Explorateur de tests en direct après avoir développé la couverture de test](media/lut-start/vs-2019/test-dynamic.png)
   ::: moniker-end

1. Basculez vers la fenêtre qui contient le code source de la classe StringLibrary. Live Unit Testing montre maintenant que la couverture de notre code est étendue à la méthode `StartsWithLower`.

    ![Couverture du code pour la méthode StartsWithLower](media/lut-start/lut-extended-cs.png)

Dans certains cas, les tests réussis dans l' **Explorateur de tests** peuvent être grisés. Cela indique qu’un test est en cours d’exécution ou que le test n’a pas été exécuté à nouveau, car il n’y a eu aucune modification de code qui aurait un impact sur le test depuis sa dernière exécution.

Jusqu’à présent, tous nos tests ont réussi. Dans la section suivante, nous allons examiner comment vous pouvez gérer l’échec d’un test.

## <a name="handle-a-test-failure"></a>Gérer l’échec d’un test

Dans cette section, vous découvrez comment vous pouvez utiliser Live Unit Testing pour identifier, dépanner et résoudre les échecs des tests. Vous faites cela en étendant la couverture de test à la méthode `HasEmbeddedSpaces`.

1. Ajoutez la méthode suivante à votre fichier de test :

   :::code language="csharp" source="../test/samples/snippets/csharp/lut-start/unittest2.cs" id="Snippet3":::

1. Quand le test s’exécute, Live Unit Testing indique que la `TestHasEmbeddedSpaces` méthode a échoué, comme le montre l’illustration suivante :

   ::: moniker range="vs-2017"
   ![L’Explorateur de tests signale un test ayant échoué](media/lut-start/test-failure.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![L’Explorateur de tests en direct signale un échec de test](media/lut-start/vs-2019/test-failure.png)
   ::: moniker-end

1. Sélectionnez la fenêtre qui affiche le code de la bibliothèque. Live Unit Testing a étendu la couverture du code à la `HasEmbeddedSpaces` méthode. Il signale également l’échec d’un test en ajoutant une croix rouge « 🞩 » pour les lignes couvertes par des tests ayant échoué.

1. Placez le curseur sur la ligne avec la signature de méthode `HasEmbeddedSpaces`. Live Unit Testing affiche une info-bulle qui indique que la méthode est couverte par un test, comme le montre l’illustration suivante :

   ![Live Unit Testing d’informations sur un test ayant échoué](media/lut-start/test-failure-info-cs.png)

1. Sélectionnez le test **TestHasEmbeddedSpaces** qui a échoué. Live Unit Testing vous donne quelques options, telles que l’exécution de tous les tests et le débogage de tous les tests, comme le montre l’illustration suivante :

   ::: moniker range="vs-2017"
   ![Options de Live Unit Testing pour un test ayant échoué](media/lut-start/test-failure-options.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Options de Live Unit Testing pour un test ayant échoué](media/lut-start/vs-2019/test-failure-options.png)
   ::: moniker-end

1. Sélectionnez **Déboguer tout** pour déboguer le test qui a échoué.

1. Visual Studio exécute le test en mode débogage.

   Le test affecte chaque chaîne d’un tableau à une variable nommée `phrase` et la passe à la `HasEmbeddedSpaces` méthode. L’exécution du programme s’interrompt et appelle le débogueur la première fois que l’expression d’assertion est `false`. La boîte de dialogue d’exception qui résulte de la valeur inattendue dans l' [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) appel de méthode est représentée dans l’illustration suivante.

   ![Boîte de dialogue d’exception de Live Unit Testing](media/lut-start/exception-dialog-cs.png)

   En outre, tous les outils de débogage fournis par Visual Studio sont disponibles pour nous aider à résoudre les problèmes liés à l’échec de notre test, comme le montre l’illustration suivante :

   ![Outils de débogage Visual Studio](media/lut-start/debugging-tools-cs.png)

   Notez que, dans la fenêtre **Automatique**, la valeur de la variable `phrase` est « Name\tDescription », qui est le deuxième élément du tableau. La méthode de test attend que `HasEmbeddedSpaces` retourne `true` quand cette chaîne lui est passée ; au lieu de cela, elle retourne `false`. De toute évidence, elle ne reconnaît pas « \t », le caractère de tabulation, comme espace incorporé.

1. Sélectionnez **Déboguer**  >  **Continuer**, appuyez sur **F5** ou cliquez sur le bouton **Continuer** dans la barre d’outils pour continuer à exécuter le programme de test. Comme une exception non gérée s’est produite, le test s’arrête.
Ceci fournit suffisamment d’informations pour un examen préliminaire du bogue. `TestHasEmbeddedSpaces` (la routine de test) a fait une supposition incorrecte ou `HasEmbeddedSpaces` ne reconnaît pas correctement tous les espaces incorporés.

1. Pour diagnostiquer et corriger le problème, commencez par la `StringLibrary.HasEmbeddedSpaces` méthode. Regardez la comparaison dans la méthode `HasEmbeddedSpaces`. Elle considère qu’un espace incorporé est représenté par U+0020. Le standard Unicode inclut plusieurs autres caractères espace. Ceci suggère que le code de la bibliothèque a été incorrectement testé pour un caractère espace.

1. Remplacez la comparaison d’égalité par un appel à la méthode <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName> :

   :::code language="csharp" source="../test/samples/snippets/csharp/lut-start/program2.cs" id="Snippet1":::

1. Live Unit Testing réexécute automatiquement la méthode de test qui a échoué.

   Live Unit Testing affiche les résultats mis à jour qui s’affichent également dans la fenêtre de l’éditeur de code.

## <a name="see-also"></a>Voir aussi

- [Live Unit Testing dans Visual Studio](live-unit-testing.md)
- [Questions fréquentes concernant Live Unit Testing](live-unit-testing-faq.yml)
