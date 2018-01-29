---
title: "Présentation de l’éditeur de Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/30/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: fd24e4ebcdda7a3b8fbc0b992e1ef952a930029a
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2018
---
# <a name="quickstart-coding-in-the-editor"></a>Démarrage rapide : Code dans l’éditeur

Dans cette présentation de 10 minutes de l’éditeur, vous allez ajouter du code dans un fichier pour découvrir de quelles façons Visual Studio facilite l’écriture, la navigation et la compréhension du code.

## <a name="create-a-new-code-file"></a>Créer un fichier de code

Vous allez commencer par créer un fichier et y ajouter du code. Notez que vous n’avez pas besoin de créer un projet pour avoir accès à certaines fonctionnalités de l’éditeur.

1. Ouvrez Visual Studio et, dans le menu **Fichier** de la barre de menus, choisissez **Nouveau** > **Fichier...**.

1. Dans la boîte de dialogue **Nouveau fichier**, sous la catégorie **Général**, choisissez **Classe Visual C#**, puis choisissez **Ouvrir**.

   Le nouveau fichier qui s’ouvre dans l’éditeur présente le squelette d’une classe C#.

## <a name="using-code-snippets"></a>Utilisation d’extraits de code

Visual Studio fournit des extraits de code qui vous aident à créer rapidement et facilement les blocs de code couramment utilisés. Ces [extraits de code](../ide/code-snippets.md) sont disponibles pour plusieurs langages de programmation, y compris C#, Visual Basic et C++. Vous allez maintenant ajouter l’extrait de code `void Main` C# dans votre fichier.

1. Placez votre curseur sous l’accolade fermante du constructeur `Class1` et entrez les caractères `svm`.

   Une boîte de dialogue IntelliSense s’affiche, avec des informations sur l’extrait de code `svm`.

   ![Extrait de code IntelliSense](media/quickstart-intellisense-snippet.png)

1. Appuyez deux fois sur **Tab** pour insérer l’extrait de code.

   La signature de la méthode `static void Main()` est ajoutée au fichier. La méthode `Main()` est le point d’entrée pour les applications C#.

Les extraits de code disponibles diffèrent selon les langages. Pour voir quels extraits de code sont disponibles pour votre langage de programmation, choisissez **Edition**, **IntelliSense**, **Insérer un extrait de code...**, puis choisissez le dossier de votre langage. Pour C#, la liste ressemble à ceci :

![Liste d’extraits de code C#](media/quickstart-code-snippet-list.png)

La liste contient des extraits de code permettant de créer une classe, un constructeur, `Console.WriteLine()`, des boucles `for`, des instructions `if` et `switch`, et bien d’autres éléments.

## <a name="commenting-out-code"></a>Commenter du code

La barre d’outils a plusieurs boutons conçus pour vous aider à écrire du code plus rapidement. Par exemple, utilisez ces boutons pour activer ou désactiver le mode de saisie semi-automatique IntelliSense, augmenter ou réduire un retrait, définir un signet ou commenter du code. Dans cette section, nous allons commenter du code que nous ne souhaitons pas compiler.

![Barre d’outils de l’éditeur](media/quickstart-editor-toolbar.png)

1. Collez le code suivant dans le corps de la méthode `Main()`.

    ```csharp
    // _words is a string array that we'll sort alphabetically
    string[] _words = {
        "the",
        "quick",
        "brown",
        "fox",
        "jumps"
    }

    string[] morewords = {
        "over",
        "the",
        "lazy",
        "dog"
    };

    IEnumerable<string> query = from word in _words
                                orderby word.Length
                                select word;
    ```

1. Nous n’avons pas besoin de la variable `morewords` ici, mais nous la conservons pour un usage ultérieur. Au lieu de cela, nous allons commenter ces lignes. Sélectionnez toute la définition de `morewords` jusqu’au point-virgule de fin, puis choisissez le bouton **Commenter les lignes sélectionnées** dans la barre d’outils, ou appuyez sur **Ctrl**+**K**, **Ctrl**+**C**.

   ![Bouton Commenter](media/quickstart-comment-out.png)

   Les caractères de commentaire C# `//` sont ajoutés au début de chaque ligne sélectionnée pour commenter le code.

## <a name="collapsing-code-blocks"></a>Réduction des blocs de code

Nous n’avons pas besoin de voir le constructeur vide de `Class1` qui a été généré. Pour plus de lisibilité, nous allons donc réduire ce bloc de code. Choisissez la petite case grise avec le signe moins qui se trouve dans la marge de la première ligne du constructeur. Si vous préférez utiliser le clavier, placez le curseur n’importe où dans le code du constructeur et appuyez sur **Ctrl**+**M**, **Ctrl**+**M**.

![Bouton de réduction du mode Plan](media/quickstart-collapse.png)

Le bloc de code est réduit de façon à afficher uniquement la première ligne, suivie de points de suspension (`...`). Pour redévelopper le bloc de code, cliquez sur la même case grise, qui affiche maintenant un signe plus, ou appuyez sur **Ctrl**+**M**, **Ctrl**+**M**  à nouveau. Cette fonctionnalité, appelée [mode Plan](../ide/outlining.md), est très utile pour réduire des méthodes longues ou des classes entières.

## <a name="viewing-symbol-definitions"></a>Affichage des définitions de symbole

L’éditeur de Visual Studio facilite l’inspection de la définition d’un type, d’une méthode, etc. Une façon de faire est d’accéder au fichier qui contient la définition, par exemple en choisissant **Atteindre la définition** à partir de n’importe quel endroit où le symbole est référencé. Une autre façon encore plus rapide, sans avoir à déplacer le focus en dehors du fichier dans lequel vous travaillez, consiste à utiliser la fonctionnalité [Aperçu de la définition](../ide/go-to-and-peek-definition.md#peek-definition). Vous allez afficher un aperçu de la définition de `string`.

1. Cliquez avec le bouton droit sur une occurrence de `string`, puis choisissez **Aperçu de la définition** dans le menu de contenu&mdash;, ou appuyez sur **Alt**+**F12**.

   Une fenêtre indépendante s’affiche, avec la définition de la classe `String`. Vous pouvez faire défiler le contenu de la fenêtre indépendante, ou même afficher un aperçu de la définition d’un autre type à partir du code en aperçu.

   ![Fenêtre Aperçu de la définition](media/quickstart-peek-definition.png)

1. Fermez la fenêtre Aperçu de la définition en choisissant la petite case avec un « x » dans le coin supérieur droit de la fenêtre indépendante.

## <a name="using-intellisense-to-complete-words"></a>Utilisation d’IntelliSense pour compléter des mots

[IntelliSense](../ide/using-intellisense.md) est une aide précieuse quand vous écrivez du code. Cette fonctionnalité peut afficher des informations sur les membres d’un type disponibles, ou les détails des paramètres des différentes surcharges d’une méthode. Vous pouvez également utiliser IntelliSense pour compléter un mot automatiquement quand vous avez tapé suffisamment de caractères pour lever toute ambiguïté sur le mot. Vous allez maintenant ajouter une ligne de code pour afficher les chaînes ordonnées dans la fenêtre de console.

1. Sous la variable `query`, commencez à taper le code suivant :

   ```csharp
   foreach (string str in qu
   ```

   IntelliSense affiche une **Info express** relative au symbole `query`.

   ![Utilisation d’IntelliSense pour compléter un mot](media/quickstart-intellisense-completion-list.png)

1. Pour insérer le reste du mot `query` en utilisant la fonctionnalité Compléter le mot d’IntelliSense, appuyez sur **Tab**.

1. Terminez le bloc de code pour obtenir le code suivant. Si vous voulez vous exercer un peu plus avec des extraits de code, entrez `cw` et appuyez deux fois sur **Tab** pour générer le code `Console.WriteLine`.

   ```csharp
   foreach (string str in query)
   {
      Console.WriteLine(str);
   }
   ```

## <a name="refactoring-a-name"></a>Refactorisation d’un nom

Aucun développeur ne réussit à créer un code parfait dès le départ. L’une de vos premières modifications sera probablement de changer le nom d’une variable ou d’une méthode. Nous allons donc essayer la fonctionnalité de [refactorisation](../ide/refactoring-in-visual-studio.md) de Visual Studio pour renommer la variable `_words` en `words`.

1. Placez votre curseur sur la définition de la variable `words`, puis choisissez **Renommer...** dans le menu contextuel (clic droit), ou appuyez sur **Ctrl**+**R**, **Ctrl**+**R**.

   Une boîte de dialogue contextuelle **Renommer** s’affiche en haut à droite de l’éditeur.

1. Entrez le nom souhaité, `words`. Notez que la référence à `words` dans la requête est également renommée automatiquement. Avant d’appuyer sur **Entrée**, cochez la case **Inclure les commentaires** dans la boîte de dialogue contextuelle **Renommer**.

   ![Renommer (boîte de dialogue)](media/quickstart-rename.png)

1. Appuyez sur **Entrée**.

   Les deux occurrences de `words` ont été renommées, tout comme la référence à `words` dans le commentaire de code.

## <a name="next-steps"></a>Étapes suivantes

Vous avez terminé ce guide de démarrage rapide pour l’éditeur de Visual Studio. Vous pouvez ensuite effectuer d’autres démarrages rapides pour l’IDE de Visual Studio, découvrir d’autres méthodes de [navigation dans le code](../ide/navigating-code.md) ou consultez les liens fournis pour en savoir plus sur les fonctionnalités que nous avons vues. Bon développement !

## <a name="see-also"></a>Voir aussi

[Démarrage rapide : premier aperçu de l'IDE Visual Studio](../ide/quickstart-ide-orientation.md)  
[Démarrage rapide : personnaliser l’éditeur et l’IDE de Visual Studio](../ide/quickstart-personalize-the-ide.md)  
[Démarrage rapide : projets et solutions](../ide/quickstart-projects-solutions.md)  
[Extraits de code](../ide/code-snippets.md)  
[Mode Plan](../ide/outlining.md)  
[Atteindre la définition et Aperçu de la définition](../ide/go-to-and-peek-definition.md)  
[Refactorisation](../ide/refactoring-in-visual-studio.md)  
[Utilisation de la fonctionnalité IntelliSense](../ide/using-intellisense.md)