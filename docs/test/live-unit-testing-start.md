---
title: Découvrir comment tester votre code avec Live Unit Test 2017
ms.date: 08/31/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 748dfc592fbf7a3b9737e9f418362067b92bb8ff
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594290"
---
# <a name="get-started-with-live-unit-testing"></a>Bien démarrer avec Live Unit Testing

Lorsque vous activez live Unit Testing dans une solution Visual Studio, il représente visuellement votre couverture de test et l’état de vos tests. Live Unit Testing exécute également dynamiquement les tests chaque fois que vous modifiez votre code et vous informe immédiatement lorsque vos modifications font échouer les tests.

Live Unit Testing peut être utilisé pour tester des solutions qui ciblent soit .NET Framework ou .NET Core. Dans ce tutoriel, vous apprendrez à utiliser Live Unit Testing en créant une simple bibliothèque de classe qui cible .NET Standard, et vous allez créer un projet MSTest qui cible .NET Core pour le tester.

La solution C# complète peut être téléchargée à partir du dépôt GitHub [MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/).

## <a name="prerequisites"></a>Conditions préalables requises

Ce tutoriel exige que vous ayez installé Visual Studio Enterprise édition avec la charge de travail **de développement multi-plateformes .NET Core.**

## <a name="create-the-solution-and-the-class-library-project"></a>Créer la solution et le projet de bibliothèque de classes

Commencez par créer une solution Visual Studio nommée UtilityLibraries qui se compose d’un seul projet de bibliothèque de classe Standard .NET, StringLibrary.

La solution est simplement un conteneur pour un ou plusieurs projets. Pour créer une solution vide, ouvrez Visual Studio et effectuez les étapes suivantes :

1. Sélectionnez **File** > **New** > **Project** dans le menu Visual Studio de haut niveau.

1. Tapez **solution** dans la zone de recherche des modèles, puis sélectionnez le modèle **Solution vide**.

   ::: moniker range="vs-2017"

   ![Boîte de dialogue **Nouveau projet**](./media/lut-start/new-solution.png)

   ::: moniker-end

1. Terminez la création de la solution.

Maintenant que vous avez créé la solution, vous allez créer une bibliothèque de classe nommée StringLibrary qui contient un certain nombre de méthodes d’extension pour travailler avec des cordes.

1. Dans **Solution Explorer**, cliquez à droite sur la solution UtilityLibraries et **sélectionnez Ajouter** > **un nouveau projet**.

::: moniker range="vs-2017"

2. Dans la boîte de dialogue **Ajouter un nouveau projet**, sélectionnez le nœud C#, puis sélectionnez **.NET Standard**.

   > [!NOTE]
   > Parce que notre bibliothèque cible .NET Standard plutôt que d’une mise en œuvre .NET particulière, il peut être appelé à partir de toute mise en œuvre .NET qui prend en charge cette version de .NET Standard. Pour plus d'informations, consultez [.NET Standard](/dotnet/standard/net-standard).

3. Sélectionnez le modèle **De bibliothèque de classe (.NET Standard)** dans le volet droit, et entrez **StringLibrary** dans la boîte à texte **Nom,** comme l’image suivante montre :

   ![Boîte de dialogue **Ajouter un nouveau projet**](./media/lut-start/add-project-cs.png)

4. Sélectionnez **OK** pour créer le projet.

::: moniker-end

::: moniker range=">=vs-2019"

2. Tapez **bibliothèque de classes** dans la zone de recherche des modèles, puis sélectionnez le modèle **Bibliothèque de classes (.NET Standard)**. Cliquez sur **Suivant**.

   > [!NOTE]
   > Parce que notre bibliothèque cible .NET Standard plutôt que d’une mise en œuvre .NET particulière, il peut être appelé à partir de toute mise en œuvre .NET qui prend en charge cette version de .NET Standard. Pour plus d'informations, consultez [.NET Standard](/dotnet/standard/net-standard).

3. Nommez le projet **StringLibrary**.

4. Cliquez sur **Créer** pour créer le projet.

::: moniker-end

5. Remplacez tout le code existant dans la fenêtre de code par le code suivant :

   [!code-csharp[StringLibrary source code](samples/csharp/utilitylibraries/stringlibrary/class1.cs)]

   StringLibrary a trois méthodes statiques :

   - `StartsWithUpper` retourne `true` si une chaîne commence par un caractère majuscule ; sinon, elle retourne `false`.

   - `StartsWithLower` retourne `true` si une chaîne commence par un caractère minuscule ; sinon, elle retourne `false`.

   - `HasEmbeddedSpaces` retourne `true` si une chaîne contient un espace incorporé ; sinon, elle retourne `false`.

6. Sélectionnez **Build** > **Build Solution** dans le menu Visual Studio de haut niveau. La construction devrait réussir.

## <a name="create-the-test-project"></a>Créer le projet de test

L’étape suivante consiste à créer le projet d’essai unitaire pour tester la bibliothèque StringLibrary. Créez les tests unitaires en procédant comme suit :

1. Dans **Solution Explorer**, cliquez à droite sur la solution UtilityLibraries et **sélectionnez Ajouter** > **un nouveau projet**.

::: moniker range="vs-2017"

2. Dans la boîte de dialogue **Ajouter un nouveau projet**, sélectionnez le nœud C#, puis sélectionnez **.NET Core**.

   > [!NOTE]
   > Vous ne devez pas nécessairement écrire vos tests unitaires dans le même langage que celui de votre bibliothèque de classes.

3. Sélectionnez le modèle **du projet de test unitaire (.NET Core)** dans le volet droit et entrez **StringLibraryTests** dans la boîte à texte **Name,** comme le montre l’image suivante :

   ![Boîte de dialogue **Ajouter un nouveau projet** pour le projet de test unitaire](./media/lut-start/add-unit-test-cs.png)

4. Sélectionnez **OK** pour créer le projet.

::: moniker-end

::: moniker range=">=vs-2019"

2. Tapez **test unitaire** dans la zone de recherche des modèles, puis sélectionnez le modèle **Projet de Test unitaire (.NET Core)**. Cliquez sur **Suivant**.

3. Nommez le projet **StringLibraryTests**.

4. Cliquez sur **Créer** pour créer le projet.

::: moniker-end

   > [!NOTE]
   > Ce didacticiel de démarrage utilise Live Unit Testing avec le framework de test MSTest. Vous pouvez également utiliser les frameworks de test xUnit et NUnit.

5. Le projet de test unitaire ne peut pas accéder automatiquement à la bibliothèque de classes qu’il teste. Vous donnez l’accès à la bibliothèque test en ajoutant une référence au projet de bibliothèque de classes. Pour ce faire, cliquez `StringLibraryTests` à droite sur le projet et sélectionnez **Ajouter** > **référence**. Dans le dialogue **du gestionnaire de référence,** assurez-vous que l’onglet **Solution** est sélectionné et sélectionnez le projet StringLibrary, tel qu’indiqué dans l’image suivante.

   ![Boîte de dialogue **Gestionnaire de références**](./media/lut-start/add-reference.png)

6. Remplacez le code de test unitaire réutilisable fourni par le modèle par le code suivant :

   [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest1.cs)]

7. Enregistrez votre projet en sélectionnant l’icône **Enregistrer** dans la barre d’outils.

8. Étant donné que le code de test unitaire inclut certains caractères non-ASCII, Visual Studio affiche le dialogue suivant pour avertir que certains caractères seront perdus si vous enregistrez le fichier dans son format ASCII par défaut. Choisissez le bouton **Enregistrer avec un autre encodage**.

   ![Choisir un encodage de fichier](media/lut-start/ascii-encoding.png)

9. Dans la liste d’abandon de **Codage** du dialogue **Advance Save Options,** choisissez **Unicode (UTF-8 sans signature) - Codepage 65001**, comme le montre l’image suivante :

   ![Choix de l’encodage UTF-8](media/lut-start/utf8-encoding.png)

10. Compilez le projet de test unitaire en sélectionnant **Build** > **Rebuild Solution** à partir du menu Visual Studio de haut niveau.

Vous avez créé une bibliothèque de classes, ainsi que quelques tests unitaires pour celle-ci. Vous avez maintenant terminé les préliminaires nécessaires pour utiliser Live Unit Testing.

## <a name="enable-live-unit-testing"></a>Activer Live Unit Testing

Jusqu’à présent, bien que vous ayez écrit les tests pour la bibliothèque de classe StringLibrary, vous ne les avez pas exécutés. Live Unit Testing les exécute automatiquement une fois que vous l’activez. Pour cela, procédez comme suit :

1. Optionnellement, sélectionnez la fenêtre de code qui contient le code pour StringLibrary. Il s’agit soit *Class1.cs* pour un projet C ou *Class1.vb* pour un projet Visual Basic. (Cette étape vous permet d’inspecter visuellement le résultat de vos tests et l’étendue de votre couverture de code une fois que vous activez le test d’unité en direct.)

1. Sélectionnez **Test** > **Live Unit Testing** > **Start** à partir du menu Visual Studio de haut niveau.

1. Visual Studio démarre Live Unit Test, qui exécute automatiquement tous vos tests.

Quand il a terminé l’exécution de vos tests, **l’Explorateur de tests** affiche les résultats globaux et les résultats des tests individuels. En outre, la fenêtre de code affiche graphiquement la couverture de votre code de test et le résultat de vos tests. Comme le montre l’image suivante, les trois tests ont été exécutés avec succès. Elle montre également que nos tests ont couvert tous les chemins de code de la méthode `StartsWithUpper`, et que ces tests ont tous été exécutés avec succès (ce qui est indiqué par la coche verte, « ✓ »). Enfin, il montre qu’aucune des autres méthodes de StringLibrary n’a de couverture de code (qui est indiquée par une ligne bleue, "➖").

![L’Explorateur de tests et la fenêtre de code après le démarrage de Live Unit Testing](media/lut-start/lut-results-cs.png)

Vous pouvez également obtenir des informations plus détaillées sur la couverture des tests et sur les résultats des tests en sélectionnant une icône de couverture de code particulière dans la fenêtre de code. Pour examiner ces informations détaillées, procédez comme suit :

1. Cliquez sur la marque de coche verte pour la ligne qui contient `if (String.IsNullOrWhiteSpace(s))` dans la méthode `StartsWithUpper`. Comme le montre l’image suivante, Live Unit Testing indique que trois tests couvrent cette ligne de code, et que tous ont exécuté avec succès.

   ![Couverture du code pour l’instruction conditionnelle « if »](media/lut-start/code-coverage-cs1.png)

1. Cliquez sur la marque de coche verte pour la ligne qui contient `return Char.IsUpper(s[0])` dans la méthode `StartsWithUpper`. Comme le montre l’image suivante, Live Unit Testing indique que seulement deux tests couvrent cette ligne de code, et que tous ont exécuté avec succès.

   ![Couverture du code pour l’instruction return](media/lut-start/code-coverage-cs2.png)

Le principal problème identifié par Live Unit Testing est une couverture du code incomplète. Vous le résolvez dans la section suivante.

## <a name="expand-test-coverage"></a>Étendre la couverture des tests

Dans cette section, vous étendez vos tests unitaires à la méthode `StartsWithLower`. Quand vous faites cela, Live Unit Testing continue à tester dynamiquement votre code.

Pour étendre la couverture du code à la méthode `StartsWithLower`, procédez comme suit :

1. Ajoutez les méthodes `TestStartsWithLower` et `TestDoesNotStartWithLower` au fichier de code source de test de votre projet :

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#1)]

1. Modifier `DirectCallWithNullOrEmpty` la méthode en ajoutant le code [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) suivant immédiatement après l’appel à la méthode.

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#2)]

1. Live Unit Testing exécute automatiquement des tests nouveaux et modifiés quand vous modifiez votre code source. Comme le montre l’image suivante de **Test Explorer,** tous les tests, y compris les deux que vous avez ajoutés et celui que vous avez modifié, ont réussi.

   ![L’Explorateur de test après l’élargissement de la couverture des tests](media/lut-start/test-dynamic.png)

1. Passez à la fenêtre qui contient le code source pour la classe StringLibrary. Live Unit Testing montre maintenant que la couverture de notre code est étendue à la méthode `StartsWithLower`.

    ![Couverture du code pour la méthode StartsWithLower](media/lut-start/lut-extended-cs.png)

Dans certains cas, les tests réussis dans **Test Explorer** peuvent être grisés. Cela indique qu’un test est actuellement en cours d’exécution, ou que le test n’a pas exécuté à nouveau parce qu’il n’y a eu aucune modification de code qui aurait un impact sur le test depuis sa dernière exécution.

Jusqu’à présent, tous nos tests ont réussi. Dans la section suivante, nous allons examiner comment vous pouvez gérer l’échec d’un test.

## <a name="handle-a-test-failure"></a>Gérer l’échec d’un test

Dans cette section, vous découvrez comment vous pouvez utiliser Live Unit Testing pour identifier, dépanner et résoudre les échecs des tests. Vous faites cela en étendant la couverture de test à la méthode `HasEmbeddedSpaces`.

1. Ajoutez la méthode suivante à votre fichier de test :

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/unittest2.cs#3)]

1. Lorsque le test s’exécute, Live `TestHasEmbeddedSpaces` Unit Testing indique que la méthode a échoué, comme le montre l’image suivante :

   ![L’explorateur d’essai signalant un test échoué](media/lut-start/test-failure.png)

1. Sélectionnez la fenêtre qui affiche le code de la bibliothèque. Live Unit Testing a élargi `HasEmbeddedSpaces` la couverture du code à la méthode. Il signale également l’échec d’un test en ajoutant une croix rouge « 🞩 » pour les lignes couvertes par des tests ayant échoué.

1. Placez le curseur sur la ligne avec la signature de méthode `HasEmbeddedSpaces`. Live Unit Testing affiche un outil qui indique que la méthode est couverte par un test, comme le montre l’image suivante :

   ![Informations d’essai d’unité en direct sur un test échoué](media/lut-start/test-failure-info-cs.png)

1. Sélectionnez le test **TestHasEmbeddedSpaces** qui a échoué. Live Unit Testing vous offre un certain nombre d’options, telles que l’exécution de tous les tests, l’exécution des tests sélectionnés, débogage de tous les tests, et débogage des tests sélectionnés, comme le montre l’image suivante:

   ![Options de test d’unité en direct pour un test échoué](media/lut-start/test-failure-options.png)

1. Sélectionnez **Déboguer le test sélectionné** pour déboguer le test qui a échoué.

1. Visual Studio exécute le test en mode débogage.

   Le test attribue chaque chaîne dans un `phrase` tableau à `HasEmbeddedSpaces` une variable nommée et la transmet à la méthode. L’exécution du programme s’interrompt et appelle le débogueur la première fois que l’expression d’assertion est `false`. Le dialogue d’exception qui résulte [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) de la valeur inattendue de l’appel de méthode est indiqué dans l’image suivante.

   ![Dialogue d’exception d’essai d’unité en direct](media/lut-start/exception-dialog-cs.png)

   En outre, tous les outils de débogage que Visual Studio fournit sont disponibles pour nous aider à dépanner notre test a échoué, comme le montre l’image suivante:

   ![Outils de débogage Visual Studio](media/lut-start/debugging-tools-cs.png)

   Notez que, dans la fenêtre **Automatique**, la valeur de la variable `phrase` est « Name\tDescription », qui est le deuxième élément du tableau. La méthode de test attend que `HasEmbeddedSpaces` retourne `true` quand cette chaîne lui est passée ; au lieu de cela, elle retourne `false`. De toute évidence, elle ne reconnaît pas « \t », le caractère de tabulation, comme espace incorporé.

1. Sélectionnez **Debug** > **Continuer**, appuyez sur **F5**, ou cliquez sur le bouton **Continuer** sur la barre d’outils pour continuer à exécuter le programme de test. Comme une exception non gérée s’est produite, le test s’arrête.
Ceci fournit suffisamment d’informations pour un examen préliminaire du bogue. `TestHasEmbeddedSpaces` (la routine de test) a fait une supposition incorrecte ou `HasEmbeddedSpaces` ne reconnaît pas correctement tous les espaces incorporés.

1. Pour diagnostiquer et corriger le `StringLibrary.HasEmbeddedSpaces` problème, commencez par la méthode. Regardez la comparaison dans la méthode `HasEmbeddedSpaces`. Elle considère qu’un espace incorporé est représenté par U+0020. Le standard Unicode inclut plusieurs autres caractères espace. Ceci suggère que le code de la bibliothèque a été incorrectement testé pour un caractère espace.

1. Remplacez la comparaison d’égalité par un appel à la méthode <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName> :

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/program2.cs#1)]

1. Live Unit Testing réexécute automatiquement la méthode de test échouée et met à jour les résultats dans la fenêtre de code et dans **Test Explorer**, comme le montre l’image suivante :

    ![Test HasEmbeddedSpaces réussi](media/lut-start/test-success-cs.png)

## <a name="see-also"></a>Voir aussi

- [Live Unit Testing dans Visual Studio](live-unit-testing.md)
- [Questions fréquentes concernant Live Unit Testing](live-unit-testing-faq.md)
