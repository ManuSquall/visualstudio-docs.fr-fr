---
title: Découvrir comment tester votre code avec Live Unit Test 2017
ms.date: 08/31/2017
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: 3082f2a3acaac7b874f98d675ae28d11ea0374ae
ms.sourcegitcommit: 87d7123c09812534b7b08743de4d11d6433eaa13
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57223768"
---
# <a name="get-started-with-live-unit-testing-in-visual-studio"></a>Bien démarrer avec Live Unit Testing dans Visual Studio

Quand vous activez Live Unit Testing dans une solution Visual Studio, il décrit la couverture et l’état de vos tests. Il exécute également dynamiquement des tests chaque fois que vous modifiez votre code et vous avertit immédiatement quand vos modifications provoquent l’échec des tests.

Live Unit Testing peut être utilisé pour tester des solutions qui ciblent le .NET Framework ou .NET Core. Dans ce didacticiel, vous découvrez comment utiliser Live Unit Testing en créant une bibliothèque de classes simple qui cible .NET Standard, et vous créez un projet MSTest qui cible .NET Core pour le tester.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

La solution C# complète peut être téléchargée à partir du dépôt GitHub [MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/).

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

La solution Visual Basic complète peut être téléchargée à partir du dépôt GitHub [MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/visual-basic/UtilityLibraries/).

---

## <a name="prerequisites"></a>Prérequis

Ce tutoriel nécessite que Visual Studio Enterprise Edition soit installé avec la charge de travail .NET Core 2.0.

## <a name="create-the-solution-and-the-class-library-project"></a>Créer la solution et le projet de bibliothèque de classes

Commencez par créer une solution Visual Studio nommée `UtilityLibraries`, qui se compose d’un projet de bibliothèque de classes .NET Standard unique, `StringLibrary`. Vous pouvez écrire `StringLibrary` en C# ou Visual Basic.

La solution est simplement un conteneur pour un ou plusieurs projets. Pour créer la solution, ouvrez Visual Studio et effectuez les étapes suivantes :

1. Sélectionnez **Fichier** > **Nouveau** > **Projet** dans le menu Visual Studio du plus haut niveau.

1. Dans la boîte de dialogue **Nouveau projet**, développez le nœud **Autres types de projets** et sélectionnez **Solutions Visual Studio**. Sélectionnez le modèle **Nouvelle Solution** dans le volet droit, puis entrez `UtilityLibraries` dans la zone de texte **Nom**, comme le montre l’illustration suivante :

   ![Boîte de dialogue **Nouveau projet**](./media/lut-start/new-solution.png)

1. Sélectionnez **OK** pour créer la solution.

Maintenant que vous avez créé la solution, vous créez une bibliothèque de classes nommée `StringLibrary`, qui contient plusieurs méthodes d’extension pour manipuler des chaînes.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur la solution `UtilityLibraries`, puis sélectionnez **Ajouter** > **Nouveau projet**.

1. Dans la boîte de dialogue **Ajouter un nouveau projet**, sélectionnez le nœud C#, puis sélectionnez **.NET Standard**.

   > [!NOTE]
   > Comme notre bibliothèque cible .NET Standard au lieu d’une implémentation particulière de .NET, elle peut être appelée à partir de toute implémentation .NET qui prend en charge cette version de .NET Standard. Pour plus d'informations, consultez [.NET Standard](/dotnet/standard/net-standard).

1. Sélectionnez le modèle **Bibliothèque de classes (.NET Standard)** dans le volet droit, puis entrez `StringLibrary` dans la zone de texte **Nom**, comme le montre l’illustration suivante :

   ![Boîte de dialogue **Ajouter un nouveau projet**](./media/lut-start/add-project-cs.png)

1. Sélectionnez **OK** pour créer le projet.

1. Remplacez tout le code existant dans la fenêtre de code par le code suivant :

   [!code-csharp[StringLibrary source code](samples/csharp/utilitylibraries/stringlibrary/class1.cs)]

   `StringLibrary` a trois méthodes statiques :

      - `StartsWithUpper` retourne `true` si une chaîne commence par un caractère majuscule ; sinon, elle retourne `false`.

      - `StartsWithLower` retourne `true` si une chaîne commence par un caractère minuscule ; sinon, elle retourne `false`.

      - `HasEmbeddedSpaces` retourne `true` si une chaîne contient un espace incorporé ; sinon, elle retourne `false`.

1. Sélectionnez **Générer** > **Générer la solution** dans le menu Visual Studio du plus haut niveau. Visual Studio doit normalement générer correctement votre bibliothèque.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur la solution `UtilityLibraries`, puis sélectionnez **Ajouter** > **Nouveau projet**.

1. Dans la boîte de dialogue **Ajouter un nouveau projet**, sélectionnez le nœud Visual Basic, puis sélectionnez **.NET Standard**.

   > [!NOTE]
   > Comme notre bibliothèque cible .NET Standard au lieu d’une implémentation particulière de .NET, elle peut être appelée à partir de toute implémentation .NET qui prend en charge cette version de .NET Standard. Pour plus d'informations, consultez [.NET Standard](/dotnet/standard/net-standard).

1. Sélectionnez le modèle **Bibliothèque de classes (.NET Standard)** dans le volet droit, puis entrez `StringLibrary` dans la zone de texte **Nom**, comme le montre l’illustration suivante :

   ![Boîte de dialogue **Ajouter un nouveau projet**](./media/lut-start/add-project-vb.png)

1. Sélectionnez **OK** pour créer le projet.

1. Remplacez tout le code existant dans la fenêtre de code par le code suivant :

   [!code-vb[StringLibrary source code](samples/visual-basic/utilitylibraries/stringlibrary/class1.vb)]

   `StringLibrary` a trois méthodes statiques :

      - `StartsWithUpper` retourne `true` si une chaîne commence par un caractère majuscule ; sinon, elle retourne `false`.

      - `StartsWithLower` retourne `true` si une chaîne commence par un caractère minuscule ; sinon, elle retourne `false`.

      - `HasEmbeddedSpaces` retourne `true` si une chaîne contient un espace incorporé ; sinon, elle retourne `false`.

1. Cliquez avec le bouton droit sur le projet StringLibrary dans **l’Explorateur de solutions**, puis sélectionnez **Propriétés**. Sous l’onglet **Application**, supprimez le texte dans la zone de texte **Espace de noms racine**, comme le montre l’illustration suivante. L’espace de noms racine est défini par [l’instruction Namespace](/dotnet/visual-basic/language-reference/statements/namespace-statement) dans le code source.

   ![Boîte de dialogue Propriétés du projet pour un projet Visual Basic](./media/lut-start/vb-properties.png)

1. Sélectionnez **Générer** > **Générer la solution** dans le menu Visual Studio du plus haut niveau. Visual Studio doit normalement générer correctement votre bibliothèque.

---

## <a name="create-the-test-project"></a>Créer le projet de test

L’étape suivante consiste à créer le projet de test unitaire pour tester la bibliothèque `StringLibrary`. Créez les tests unitaires en procédant comme suit :

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur la solution `UtilityLibraries`, puis sélectionnez **Ajouter** > **Nouveau projet**.

1. Dans la boîte de dialogue **Ajouter un nouveau projet**, sélectionnez le nœud C#, puis sélectionnez **.NET Core**.

   > [!NOTE]
   > Vous ne devez pas nécessairement écrire vos tests unitaires dans le même langage que celui de votre bibliothèque de classes.

1. Sélectionnez le modèle **Projet de test unitaire (.NET Core)** dans le volet droit, puis entrez `StringLibraryTests` dans la zone de texte **Nom**, comme le montre l’illustration suivante :

   ![Boîte de dialogue **Ajouter un nouveau projet** pour le projet de test unitaire](./media/lut-start/add-unit-test-cs.png)

1. Sélectionnez **OK** pour créer le projet.

   > [!NOTE]
   > Ce didacticiel de démarrage utilise Live Unit Testing avec le framework de test MSTest. Vous pouvez également utiliser les frameworks de test xUnit et NUnit.

1. Le projet de test unitaire ne peut pas accéder automatiquement à la bibliothèque de classes qu’il teste. Vous donnez l’accès à la bibliothèque test en ajoutant une référence au projet de bibliothèque de classes. Pour cela, cliquez avec le bouton droit sur le projet `StringLibraryTests` et sélectionnez **Ajouter** > **Référence**. Dans la boîte de dialogue **Gestionnaire de références**, vérifiez que l’onglet **Solution** est sélectionné, puis sélectionnez le projet `StringLibrary`, comme indiqué dans l’illustration suivante.

   ![Boîte de dialogue **Gestionnaire de références**](./media/lut-start/add-reference.png)

1. Remplacez le code de test unitaire réutilisable fourni par le modèle par le code suivant :

   [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest1.cs)]

1. Enregistrez votre projet en sélectionnant l’icône **Enregistrer** dans la barre d’outils.

1. Comme le code des tests unitaires inclut certains caractères non-ASCII, Visual Studio affiche la boîte de dialogue pour nous avertir que certains caractères seront perdus si nous enregistrons le fichier à son format ASCII par défaut. Choisissez le bouton **Enregistrer avec un autre encodage**.

   ![Choisir un encodage de fichier](media/lut-start/ascii-encoding.png)

1. Dans la liste déroulante **Encodage** de la boîte de dialogue **Options d’enregistrement avancées**, choisissez **Unicode (UTF-8 sans signature) - Page de codes 65001**, comme illustré dans la figure suivante :

   ![Choix de l’encodage UTF-8](media/lut-start/utf8-encoding.png)

1. Compilez le projet de test unitaire en sélectionnant **Générer** > **Regénérer la solution** dans le menu Visual Studio du plus haut niveau.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur la solution `UtilityLibraries`, puis sélectionnez **Ajouter** > **Nouveau projet**.

1. Dans la boîte de dialogue **Ajouter un nouveau projet**, sélectionnez le nœud Visual Basic, puis sélectionnez **.NET Core**.

   > [!NOTE]
   > Vous ne devez pas nécessairement écrire vos tests unitaires dans le même langage que celui de votre bibliothèque de classes.

1. Sélectionnez le modèle **Projet de test unitaire (.NET Core)** dans le volet droit, puis entrez `StringLibraryTests` dans la zone de texte **Nom**, comme le montre l’illustration suivante :

   ![Boîte de dialogue **Ajouter un nouveau projet** pour le test unitaire](./media/lut-start/add-unit-test-vb.png)

1. Sélectionnez **OK** pour créer le projet.

   > [!NOTE]
   > Ce didacticiel de démarrage utilise Live Unit Testing avec le framework de test MSTest. Vous pouvez également utiliser les frameworks de test xUnit et NUnit.

1. Le projet de test unitaire ne peut pas accéder automatiquement à la bibliothèque de classes qu’il teste. Vous donnez l’accès à la bibliothèque test en ajoutant une référence au projet de bibliothèque de classes. Pour cela, cliquez avec le bouton droit sur le projet `StringLibraryTests` et sélectionnez **Ajouter** > **Référence**. Dans la boîte de dialogue **Gestionnaire de références**, vérifiez que l’onglet **Solution** est sélectionné, puis sélectionnez le projet `StringLibrary`, comme indiqué dans l’illustration suivante.

   ![Boîte de dialogue **Gestionnaire de références**](./media/lut-start/add-reference.png)

1. Remplacez le code de test unitaire réutilisable fourni par le modèle par le code suivant :

   [!code-vb[StringLibraryTest source code](samples/snippets/visual-basic/lut-start/unittest1.vb)]

1. Enregistrez votre projet en sélectionnant l’icône **Enregistrer** dans la barre d’outils.

1. Comme le code des tests unitaires inclut certains caractères non-ASCII, Visual Studio affiche la boîte de dialogue pour nous avertir que certains caractères seront perdus si nous enregistrons le fichier à son format ASCII par défaut. Choisissez le bouton **Enregistrer avec un autre encodage**.

   ![Choisir un encodage de fichier](media/lut-start/ascii-encoding.png)

1. Dans la liste déroulante **Encodage** de la boîte de dialogue **Options d’enregistrement avancées**, choisissez **Unicode (UTF-8 sans signature) - Page de codes 65001**, comme illustré dans la figure suivante :

   ![Choix de l’encodage UTF-8](media/lut-start/utf8-encoding.png)

1. Compilez le projet de test unitaire en choisissant **Générer** > **Regénérer la solution** dans le menu Visual Studio du plus haut niveau.

---

Vous avez créé une bibliothèque de classes, ainsi que quelques tests unitaires pour celle-ci. Vous avez maintenant terminé les préliminaires nécessaires pour utiliser Live Unit Testing.

## <a name="enable-live-unit-testing"></a>Activer Live Unit Testing

Jusqu’ici, bien que vous ayez écrit les tests pour la bibliothèque de classes `StringLibrary`, vous ne les avez pas exécutés. Live Unit Testing les exécute automatiquement une fois que vous l’activez. Pour cela, procédez comme suit :

1. Si vous le souhaitez, sélectionnez la fenêtre de code qui contient le code pour `StringLibrary`. Il s’agit de *Class1.cs* pour un projet C# ou de *Class1.vb* pour un projet Visual Basic. (Cette étape vous permet d’inspecter visuellement le résultat de vos tests et l’étendue de la couverture de votre code une fois que vous activez Live Unit Testing.)

1. Sélectionnez **Tester** > **Live Unit Testing** > **Démarrer** dans le menu Visual Studio du plus haut niveau.

1. Visual Studio démarre Live Unit Test, qui exécute automatiquement tous vos tests.

Quand il a terminé l’exécution de vos tests, **l’Explorateur de tests** affiche les résultats globaux et les résultats des tests individuels. En outre, la fenêtre de code affiche graphiquement la couverture de votre code de test et le résultat de vos tests. Comme le montre l’illustration suivante, les trois tests ont été exécutés avec succès. Elle montre également que nos tests ont couvert tous les chemins de code de la méthode `StartsWithUpper`, et que ces tests ont tous été exécutés avec succès (ce qui est indiqué par la coche verte, « ✓ »). Elle montre enfin qu’aucune autre méthode dans `StringLibrary` ne dispose d’une couverture du code (indiquée par une ligne bleue, « ➖ »).

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

![L’Explorateur de tests et la fenêtre de code après le démarrage de Live Unit Testing](media/lut-start/lut-results-cs.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

![L’Explorateur de tests et la fenêtre de code après le démarrage de Live Unit Testing](media/lut-start/lut-results-vb.png)

---

Vous pouvez également obtenir des informations plus détaillées sur la couverture des tests et sur les résultats des tests en sélectionnant une icône de couverture de code particulière dans la fenêtre de code. Pour examiner ces informations détaillées, procédez comme suit :

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Cliquez sur la marque de coche verte pour la ligne qui contient `if (String.IsNullOrWhiteSpace(s))` dans la méthode `StartsWithUpper`. Comme le montre l’illustration suivante, Live Unit Testing indique que trois tests couvrent cette ligne de code, et que tous ont été exécutés avec succès.

   ![Couverture du code pour l’instruction conditionnelle « if »](media/lut-start/code-coverage-cs1.png)

1. Cliquez sur la marque de coche verte pour la ligne qui contient `return Char.IsUpper(s[0])` dans la méthode `StartsWithUpper`. Comme le montre l’illustration suivante, Live Unit Testing indique que seuls deux tests couvrent cette ligne de code, et que tous ont été exécutés avec succès.

   ![Couverture du code pour l’instruction return](media/lut-start/code-coverage-cs2.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Cliquez sur la marque de coche verte pour la ligne qui contient `If (String.IsNullOrWhiteSpace(s)) Then` dans la méthode `StartsWithUpper`. Comme le montre l’illustration suivante, Live Unit Testing indique que trois tests couvrent cette ligne de code, et que tous ont été exécutés avec succès.

   ![Couverture du code pour l’instruction conditionnelle « If »](media/lut-start/code-coverage-vb1.png)

1. Cliquez sur la marque de coche verte pour la ligne qui contient `Return Char.IsUpper(s(0))` dans la méthode `StartsWithUpper`. Comme le montre l’illustration suivante, Live Unit Testing indique que seuls deux tests couvrent cette ligne de code, et que tous ont été exécutés avec succès.

   ![Couverture du code pour l’instruction return](media/lut-start/code-coverage-vb2.png)

---

Le principal problème identifié par Live Unit Testing est une couverture du code incomplète. Vous le résolvez dans la section suivante.

## <a name="expand-test-coverage"></a>Étendre la couverture des tests

Dans cette section, vous étendez vos tests unitaires à la méthode `StartsWithLower`. Quand vous faites cela, Live Unit Testing continue à tester dynamiquement votre code.

Pour étendre la couverture du code à la méthode `StartsWithLower`, procédez comme suit :

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Ajoutez les méthodes `TestStartsWithLower` et `TestDoesNotStartWithLower` au fichier de code source de test de votre projet :

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#1)]

1. Modifiez la méthode `DirectCallWithNullOrEmpty` en ajoutant le code suivant immédiatement après l’appel à la méthode [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse).

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#2)]

1. Live Unit Testing exécute automatiquement des tests nouveaux et modifiés quand vous modifiez votre code source. Comme le montre la figure ci-après de **l’Explorateur de tests**, tous les tests, y compris les deux tests que vous avez ajoutés et celui que vous avez modifié, ont réussi.

   ![L’Explorateur de tests après l’extension de la couverture des tests.](media/lut-start/test-dynamic.png)

1. Passez à la fenêtre qui contient le code source pour la classe `StringLibrary`. Live Unit Testing montre maintenant que la couverture de notre code est étendue à la méthode `StartsWithLower`.

    ![Couverture du code pour la méthode StartsWithLower](media/lut-start/lut-extended-cs.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Ajoutez les méthodes `TestStartsWithLower` et `TestDoesNotStartWithLower` au fichier de code source de test de votre projet :

    [!code-vb[StringLibraryTest source code](samples/snippets/visual-basic/lut-start/unittest2.vb#1)]

1. Modifiez la méthode `DirectCallWithNullOrEmpty` en ajoutant le code suivant immédiatement après l’appel à la méthode [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse).

    [!code-vb[StringLibraryTest source code](samples/snippets/visual-basic/lut-start/unittest2.vb#2)]

1. Live Unit Testing exécute automatiquement des tests nouveaux et modifiés quand vous modifiez votre code source. Comme le montre la figure ci-après de **l’Explorateur de tests**, tous les tests, y compris les deux tests que vous avez ajoutés et celui que vous avez modifié, ont réussi.

   ![L’Explorateur de tests après l’extension de la couverture des tests.](media/lut-start/test-dynamic.png)

1. Passez à la fenêtre qui contient le code source pour la classe `StringLibrary`. Live Unit Testing montre maintenant que la couverture de notre code est étendue à la méthode `StartsWithLower`.

    ![Couverture du code pour la méthode StartsWithLower](media/lut-start/lut-extended-vb.png)

---

Dans certains cas, des tests réussis dans **l’Explorateur de tests** peuvent apparaître en grisé. Ceci indique qu’un test est en cours d’exécution ou que le test n’a pas été réexécuté, car il n’y a pas eu de modification du code impactant le test depuis sa dernière exécution.

Jusqu’à présent, tous nos tests ont réussi. Dans la section suivante, nous allons examiner comment vous pouvez gérer l’échec d’un test.

## <a name="handle-a-test-failure"></a>Gérer l’échec d’un test

Dans cette section, vous découvrez comment vous pouvez utiliser Live Unit Testing pour identifier, dépanner et résoudre les échecs des tests. Vous faites cela en étendant la couverture de test à la méthode `HasEmbeddedSpaces`.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Ajoutez la méthode suivante à votre fichier de test :

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/unittest2.cs#3)]

1. Quand le test s’exécute, Live Unit Testing indique que la méthode `TestHasEmbeddedSpaces` a échoué, comme le montre la figure suivante :

   ![L’Explorateur de tests signalant un test en échec.](media/lut-start/test-failure.png)

1. Sélectionnez la fenêtre qui affiche le code de la bibliothèque. Notez que Live Unit Testing a étendu la couverture du code à la méthode `HasEmbeddedSpaces`. Il signale également l’échec d’un test en ajoutant une croix rouge « 🞩 » pour les lignes couvertes par des tests ayant échoué.

1. Placez le curseur sur la ligne avec la signature de méthode `HasEmbeddedSpaces`. Live Unit Testing affiche une info-bulle qui indique que la méthode est couverte par un test, comme le montre l’illustration suivante :

   ![Informations de Live Unit Testing sur un test ayant échoué.](media/lut-start/test-failure-info-cs.png)

1. Sélectionnez le test **TestHasEmbeddedSpaces** qui a échoué. Notez que Live Unit Testing vous offre plusieurs options, comme exécuter tous les tests, exécuter les tests sélectionnés, déboguer tous les tests et déboguer des tests sélectionnés, comme la figure suivante le montre :

   ![Options de Live Unit Testing pour un test ayant échoué.](media/lut-start/test-failure-options.png)

1. Sélectionnez **Déboguer le test sélectionné** pour déboguer le test qui a échoué.

1. Visual Studio exécute le test en mode débogage. Notre test affecte chaque chaîne dans un tableau à une variable nommée `phrase` et la passe à la méthode `HasEmbeddedSpaces`. L’exécution du programme s’interrompt et appelle le débogueur la première fois que l’expression d’assertion est `false`. La boîte de dialogue d’exception résultant de la valeur inattendue dans l’appel de méthode [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) est montrée dans la figure suivante.

   ![Boîte de dialogue d’exception de Live Unit Testing.](media/lut-start/exception-dialog-cs.png)

   En outre, tous les outils de débogage fournis par Visual Studio sont disponibles pour nous aider à résoudre les problèmes de notre test qui a échoué, comme le montre la figure suivante :

   ![Outils de débogage de Visual Studio.](media/lut-start/debugging-tools-cs.png)

   Notez que, dans la fenêtre **Automatique**, la valeur de la variable `phrase` est « Name\tDescription », qui est le deuxième élément du tableau. La méthode de test attend que `HasEmbeddedSpaces` retourne `true` quand cette chaîne lui est passée ; au lieu de cela, elle retourne `false`. De toute évidence, elle ne reconnaît pas « \t », le caractère de tabulation, comme espace incorporé.

1. Sélectionnez **Déboguer** > **Continuer**, appuyez sur **F5** ou cliquez sur le bouton **Continuer** dans la barre d’outils pour continuer l’exécution du programme de test. Comme une exception non gérée s’est produite, le test s’arrête.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Ajoutez la méthode suivante à votre fichier de test :

    [!code-vb[The TestHasEmbeddedSpaces test method](samples/snippets/visual-basic/lut-start/unittest2.vb#3)]

1. Quand le test s’exécute, Live Unit Testing indique que la méthode `TestHasEmbeddedSpaces` a échoué, comme le montre la figure suivante :

   ![L’Explorateur de tests signalant un test en échec.](media/lut-start/test-failure.png)

1. Sélectionnez la fenêtre qui affiche le code de la bibliothèque. Notez que Live Unit Testing a étendu la couverture du code à la méthode `HasEmbeddedSpaces`. Il signale également l’échec d’un test en ajoutant une croix rouge « 🞩 » pour les lignes couvertes par des tests ayant échoué.

1. Placez le curseur sur la ligne avec la signature de méthode `HasEmbeddedSpaces`. Live Unit Testing affiche une info-bulle qui indique que la méthode est couverte par un test, comme le montre l’illustration suivante :

   ![Informations de Live Unit Testing sur un test ayant échoué.](media/lut-start/test-failure-info-vb.png)

1. Sélectionnez le test **TestHasEmbeddedSpaces** qui a échoué. Notez que Live Unit Testing vous offre plusieurs options, comme exécuter tous les tests, exécuter les tests sélectionnés, déboguer tous les tests et déboguer des tests sélectionnés, comme la figure suivante le montre :

   ![Options de Live Unit Testing pour un test ayant échoué.](media/lut-start/test-failure-options.png)

1. Sélectionnez **Déboguer le test sélectionné** pour déboguer le test qui a échoué.

1. Visual Studio exécute le test en mode débogage. Notre test affecte chaque chaîne dans un tableau à une variable nommée `phrase` et la passe à la méthode `HasEmbeddedSpaces`. L’exécution du programme s’interrompt et appelle le débogueur la première fois que l’expression d’assertion est `false`. La boîte de dialogue d’exception résultant de la valeur inattendue dans l’appel de méthode [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) est montrée dans la figure suivante.

   ![Boîte de dialogue d’exception de Live Unit Testing.](media/lut-start/exception-dialog-vb.png)

   En outre, tous les outils de débogage fournis par Visual Studio sont disponibles pour nous aider à résoudre les problèmes de notre test qui a échoué, comme le montre la figure suivante :

   ![Outils de débogage de Visual Studio.](media/lut-start/debugging-tools-vb.png)

   Notez que, dans la fenêtre **Automatique**, la valeur de la variable `phrase` est « Name » + vbTab + « Description », qui est le deuxième élément du tableau. La méthode de test attend que `HasEmbeddedSpaces` retourne `true` quand cette chaîne lui est passée ; au lieu de cela, elle retourne `false`. De toute évidence, elle ne reconnaît pas le caractère de tabulation comme espace incorporé.

1. Sélectionnez **Déboguer** > **Continuer**, appuyez sur **F5** ou cliquez sur le bouton **Continuer** dans la barre d’outils pour continuer l’exécution du programme de test. Comme une exception non gérée s’est produite, le test s’arrête.

---

Ceci fournit suffisamment d’informations pour un examen préliminaire du bogue. `TestHasEmbeddedSpaces` (la routine de test) a fait une supposition incorrecte ou `HasEmbeddedSpaces` ne reconnaît pas correctement tous les espaces incorporés. Pour diagnostiquer et corriger le problème, commencez par la méthode `StringLibrary.HasEmbeddedSpaces` :

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Regardez la comparaison dans la méthode `HasEmbeddedSpaces`. Elle considère qu’un espace incorporé est représenté par U+0020. Le standard Unicode inclut plusieurs autres caractères espace. Ceci suggère que le code de la bibliothèque a été incorrectement testé pour un caractère espace.

1. Remplacez la comparaison d’égalité par un appel à la méthode <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName> :

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/program2.cs#1)]

1. Live Unit Testing réexécute automatiquement la méthode du test en échec et met à jour les résultats dans la fenêtre de code et dans **l’Explorateur de tests**, comme le montre la figure suivante :

    ![Le test HasEmbeddedSpaces réussi.](media/lut-start/test-success-cs.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Regardez la comparaison dans la méthode `HasEmbeddedSpaces`. Elle considère qu’un espace incorporé est représenté par U+0020. Le standard Unicode inclut plusieurs autres caractères espace. Ceci suggère que le code de la bibliothèque a été incorrectement testé pour un caractère espace.

1. Remplacez la comparaison d’égalité par un appel à la méthode <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName> :

    [!code-vb[The TestHasEmbeddedSpaces test method](samples/snippets/visual-basic/lut-start/class2.vb#1)]

1. Live Unit Testing réexécute automatiquement la méthode du test en échec et met à jour les résultats dans la fenêtre de code et dans **l’Explorateur de tests**, comme le montre la figure suivante :

    ![Le test HasEmbeddedSpaces réussi.](media/lut-start/test-success-vb.png)

---

## <a name="see-also"></a>Voir aussi

- [Live Unit Testing dans Visual Studio](live-unit-testing.md)
- [Questions fréquentes (FAQ) sur Live Unit Testing](live-unit-testing-faq.md)