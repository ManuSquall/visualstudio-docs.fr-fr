---
title: Introduction à la modification pour les développeurs Visual Basic
description: Cette présentation de 10 minutes de l’éditeur de code de Visual Studio montre de quelles façons Visual Studio facilite l’écriture, la navigation et la compréhension du code Visual Basic.
ms.custom: seodec18, get-started
ms.date: 11/20/2018
ms.technology: vs-ide-general
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 56f6570b633941c8f7102e245b7668cd31936f83
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308361"
---
# <a name="learn-to-use-the-code-editor-with-visual-basic"></a>En savoir plus sur l’utilisation de l’éditeur de code avec Visual Basic

Dans cette présentation de 10 minutes de l’éditeur de code de Visual Studio, nous allons ajouter du code à un fichier pour examiner certaines façons dont Visual Studio facilite l’écriture, la navigation et la compréhension du code Visual Basic.

::: moniker range="vs-2017"

> [!TIP]
> Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) pour l’installer gratuitement.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads) pour l’installer gratuitement.

::: moniker-end

::: moniker range="vs-2022"

> [!TIP]
> Si vous n’avez pas encore installé Visual Studio Preview, accédez à la page [téléchargements Visual studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) pour l’installer gratuitement.

::: moniker-end

Cet article part du principe que vous connaissez déjà Visual Basic. Si ce n’est pas le cas, nous vous suggérons de consulter un tutoriel comme [Bien démarrer avec Visual Basic dans Visual Studio](../../get-started/visual-basic/tutorial-console.md) pour commencer.

> [!TIP]
> Pour suivre cet article, vérifiez que vous avez sélectionné les paramètres Visual Basic pour Visual Studio. Pour plus d’informations sur la sélection des paramètres pour l’environnement de développement intégré (IDE), consultez [Sélectionner les paramètres d’environnement](visual-studio-ide.md#select-environment-settings).

## <a name="create-a-new-code-file"></a>Créer un fichier de code

Vous allez commencer par créer un fichier et y ajouter du code.

::: moniker range="vs-2017"

1. Ouvrez Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

1. Ouvrez Visual Studio. Appuyez sur **Échap** ou cliquez sur **Continuer sans code** dans la fenêtre de démarrage pour ouvrir l’environnement de développement.

::: moniker-end

2. Dans le menu **Fichier** de la barre de menus, choisissez **Nouveau Fichier**.

3. Dans la boîte de dialogue **Nouveau fichier**, sous la catégorie **Général**, choisissez **Classe Visual Basic**, puis choisissez **Ouvrir**.

   Un nouveau fichier qui s’ouvre dans l’éditeur présente le squelette d’une classe Visual Basic. (Notez que vous n’êtes pas obligés de créer un projet Visual Studio complet pour bénéficier de certains des avantages offerts par l’éditeur de code, comme la coloration syntaxique. Tout ce dont vous avez besoin c’est un fichier de code !)

   ![Fichier de code Visual Basic dans Visual Studio](media/tutorial-editor.png)

## <a name="use-code-snippets"></a>Utiliser des extraits de code

Visual Studio fournit des *extraits de code* qui vous aident à créer rapidement et facilement les blocs de code couramment utilisés. Ces [extraits de code](../../ide/code-snippets.md) sont disponibles pour plusieurs langages de programmation, y compris Visual Basic, C# et C++. Ajoutons l’extrait de code **Sub** Visual Basic à notre fichier.

1. Placez votre curseur au-dessus de la ligne indiquant `End Class` et le type **sub**.

   Une boîte de dialogue contextuelle affiche des informations sur le mot clé `Sub` et relatives à l’insertion de l’extrait de code **Sub**.

   ![IntelliSense pour l’extrait de code dans Visual Studio](media/tutorial-intellisense-snippet.png)

1. Appuyez deux fois sur **Tab** pour insérer l’extrait de code.

   La présentation de la procédure Sub `MySub()` est ajoutée au fichier.

Les extraits de code disponibles diffèrent en fonction des langages de programmation. Vous pouvez consulter les extraits de code disponibles pour Visual Basic en choisissant **modifier**  >  **IntelliSense**  >  **Insérer un extrait** (ou en appuyant sur **CTRL** + **K**, **CTRL** + **X**). Dans Visual Basic, les extraits de code sont disponibles pour les catégories suivantes :

![Liste des extraits de code Visual Basic](media/tutorial-code-snippet-list.png)

Il existe des extraits de code pour déterminer si un fichier existe sur l’ordinateur, pour écrire dans un fichier texte, pour lire une valeur de Registre, pour exécuter une requête SQL, pour créer une [instruction For Each...Next](/dotnet/visual-basic/language-reference/statements/for-each-next-statement) et bien plus encore.

## <a name="comment-out-code"></a>Commenter du code

La barre d’outils, qui est la ligne de boutons sous la barre de menus dans Visual Studio, peut aider à augmenter votre productivité quand vous codez. Par exemple, vous pouvez activer ou désactiver le mode de saisie semi-automatique IntelliSense, augmenter ou réduire un retrait d’une ligne, ou commenter du code que vous ne voulez pas compiler. ([IntelliSense](../../ide/using-intellisense.md) est une aide au codage qui affiche une liste de méthodes correspondantes, entre autres choses.) Dans cette section, nous allons commenter du code.

![Boutons de la barre d'outils de l’éditeur](media/tutorial-editor-toolbar.png)

1. Collez le code suivant dans le corps de la procédure `MySub()`.

   ```vb
   ' _words is a string array that we'll sort alphabetically
   Dim _words = New String() {
   "the",
   "quick",
   "brown",
   "fox",
   "jumps"
   }

   Dim morewords = New String() {
   "over",
   "the",
   "lazy",
   "dog"
   }

   Dim query = From word In _words
               Order By word.Length
               Select word
   ```

1. Nous n’utilisons pas le tableau `morewords`, mais nous n’allons pas le supprimer complètement car nous en aurons peut-être besoin plus tard. Au lieu de cela, nous allons commenter ces lignes. Sélectionnez toute la définition de `morewords` jusqu’à l’accolade de fin, puis choisissez le bouton **Commenter les lignes sélectionnées** dans la barre d’outils. Si vous préférez utiliser le clavier, appuyez sur **CTRL** + **K**, **CTRL** + **C**.

   ![Bouton Commenter](media/tutorial-comment-out.png)

   Le caractère de commentaire Visual Basic `'` est ajouté au début de chaque ligne sélectionnée pour commenter le code.

## <a name="collapse-code-blocks"></a>Réduire les blocs de code

Vous pouvez réduire des sections de code pour vous concentrer uniquement sur les parties qui vous intéressent. Pour nous entraîner, nous allons réduire le tableau `_words` à une seule ligne de code. Choisissez la petite case grise avec le signe moins qui se trouve dans la marge de la ligne indiquant `Dim _words = New String() {`. Ou, si vous êtes un utilisateur du clavier, placez le curseur n’importe où dans la définition du tableau et appuyez sur **CTRL** + **m**, **CTRL** + **m**.

![Bouton de réduction du mode Plan](media/tutorial-collapse.png)

Le bloc de code est réduit de façon à afficher uniquement la première ligne, suivie de points de suspension (`...`). Pour rajouter le bloc de code, cliquez sur la zone grise qui contient maintenant un signe plus (+) ou appuyez de nouveau sur **CTRL** + **m**, **CTRL** + **m** . Cette fonctionnalité, appelée [Mode Plan](../../ide/outlining.md), est très utile pour réduire des méthodes longues ou des classes entières.

## <a name="view-symbol-definitions"></a>Afficher les définitions de symbole

L’éditeur Visual Studio facilite l’inspection de la définition d’un type, d’une méthode, etc. L’une des méthodes consiste à naviguer jusqu’au fichier qui contient la définition, par exemple en choisissant **atteindre la définition** partout où le symbole est référencé. Une autre façon encore plus rapide, sans avoir à déplacer le focus en dehors du fichier dans lequel vous travaillez, consiste à utiliser la fonctionnalité [Aperçu de la définition](../../ide/go-to-and-peek-definition.md#peek-definition). Vous allez afficher un aperçu de la définition du type `String`.

1. Cliquez avec le bouton droit sur le mot `String`, puis choisissez **Aperçu de la définition** dans le menu de contenu. Ou appuyez sur **ALT** + **F12**.

   Une fenêtre indépendante s’affiche, avec la définition de la classe `String`. Vous pouvez faire défiler le contenu de la fenêtre indépendante, ou même afficher un aperçu de la définition d’un autre type à partir du code en aperçu.

   ![Fenêtre Aperçu de la définition](media/tutorial-peek-definition.png)

1. Fermez la fenêtre Aperçu de la définition en choisissant la petite case avec un « x » dans le coin supérieur droit de la fenêtre indépendante.

## <a name="use-intellisense-to-complete-words"></a>Utiliser IntelliSense pour compléter des mots

[IntelliSense](../../ide/using-intellisense.md) est une ressource précieuse lors du codage. Cette fonctionnalité peut afficher des informations sur les membres d’un type disponibles, ou les détails des paramètres des différentes surcharges d’une méthode. Vous pouvez également utiliser IntelliSense pour compléter un mot automatiquement quand vous avez tapé suffisamment de caractères pour lever toute ambiguïté sur le mot. Nous allons ajouter une ligne de code pour imprimer les chaînes ordonnées dans la fenêtre de console, qui est l’emplacement standard pour la sortie du programme.

1. Sous la variable `query`, commencez à taper le code suivant :

   ```vb
   For Each str In qu
   ```

   IntelliSense affiche une **Info express** relative au symbole `query`.

   ![Complétion de mot IntelliSense dans Visual Studio](media/tutorial-intellisense-completion-list.png)

1. Pour insérer le reste du mot `query` à l’aide la fonctionnalité de complétion de mot d’IntelliSense, appuyez sur **Tab**.

1. Terminez le bloc de code pour obtenir le code suivant.

   ```vb
   For Each str In query
       Console.WriteLine(str)
   Next
   ```

## <a name="refactor-a-name"></a>Refactoriser un nom

Aucun développeur ne réussit à créer un code parfait dès le départ. L’une de vos premières modifications sera probablement de changer le nom d’une variable ou d’une méthode. Nous allons donc essayer la fonctionnalité [Refactoriser](../../ide/refactoring-in-visual-studio.md) de Visual Studio pour renommer la variable `_words` en `words`.

1. Placez votre curseur sur la définition de la variable `_words`, puis choisissez **Renommer** dans le menu contextuel (clic droit).

   Une boîte de dialogue contextuelle **Renommer** s’affiche en haut à droite de l’éditeur.

1. Avec la variable `_words` toujours sélectionnée, tapez le nom de votre choix pour **mots**. Notez que la référence à `words` dans la requête est également renommée automatiquement. Avant d’appuyer sur **Entrée** ou de cliquer sur **Appliquer**, cochez la case **Inclure les commentaires** dans la boîte de dialogue contextuelle **Renommer**.

   ![Renommer (boîte de dialogue)](media/tutorial-rename.png)

1. Appuyez sur **Entrée** ou cliquez sur **Appliquer**.

   Les deux occurrences de `words` sont renommées, tout comme la référence à `words` dans le commentaire de code.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Découvrir les projets et les solutions](tutorial-projects-solutions.md)

## <a name="see-also"></a>Voir aussi

- [Extraits de code](../../ide/code-snippets.md)
- [Naviguer dans le code](../../ide/navigating-code.md)
- [mode Plan](../../ide/outlining.md)
- [Atteindre la définition et Aperçu de la définition](../../ide/go-to-and-peek-definition.md)
- [Refactorisation](../../ide/refactoring-in-visual-studio.md)
- [Utiliser IntelliSense](../../ide/using-intellisense.md)
