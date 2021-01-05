---
title: Introduction à la modification pour les développeurs JavaScript
description: Cette présentation de l’éditeur de code de Visual Studio montre de quelles façons Visual Studio facilite l’écriture, la navigation et la compréhension du code JavaScript.
ms.date: 12/13/2018
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: bd1b12be2dba1526301cd0ea9a4356fb9cc14c14
ms.sourcegitcommit: 105e7b5a486262bc92939980383ceee068098a11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/30/2020
ms.locfileid: "97815735"
---
# <a name="learn-to-use-the-code-editor-for-javascript"></a>En savoir plus sur l’utilisation de l’éditeur de code pour JavaScript

Dans cette présentation de l’éditeur de code de Visual Studio, nous allons découvrir de quelles façons Visual Studio facilite l’écriture, la navigation et la compréhension du code.

> [!TIP]
> Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/) pour l’installer gratuitement. Selon le type de développement d’applications que vous exécutez, vous devrez peut-être installer la **charge de travail de développement Node.js** avec Visual Studio. Pour plus d’informations sur l’obtention du service de langage pour la machine à écrire, consultez [prise en charge](../javascript/javascript-in-vs-2019.md#typescript-support)de la machine à écrire.

Cet article part du principe que vous connaissez déjà le développement JavaScript. Si ce n’est pas le cas, nous vous suggérons de consulter un tutoriel comme [Créer une application Node.js et Express](../javascript/tutorial-nodejs.md) pour commencer.

## <a name="add-a-new-project-file"></a>Ajouter un nouveau fichier de projet

Vous pouvez utiliser l’IDE pour ajouter de nouveaux fichiers à votre projet.

1. Une fois votre projet ouvert dans Visual Studio, cliquez avec le bouton droit sur un dossier ou sur le nœud de votre projet dans Explorateur de solutions (volet droit), puis choisissez **Ajouter**  >  **un nouvel élément**.

1. Dans la boîte de dialogue **Nouveau fichier**, sous la catégorie **Général**, choisissez le type de fichier que vous souhaitez ajouter, par exemple **Fichier JavaScript**, puis choisissez **Ouvrir**.

    Le nouveau fichier est ajouté à votre projet et s’ouvre dans l’éditeur.

## <a name="use-intellisense-to-complete-words"></a>Utiliser IntelliSense pour compléter des mots

IntelliSense est une aide précieuse quand vous écrivez du code. Cette fonctionnalité peut afficher des informations sur les membres d’un type disponibles, ou les détails des paramètres des différentes surcharges d’une méthode. Dans le code suivant, lorsque vous tapez `Router()`, vous voyez les types d’arguments que vous pouvez transmettre. Il s’agit d’une aide pour la signature.

![Capture d’écran d’une fenêtre de code Visual Studio avec du code JavaScript en cours d’entrée. Les informations IntelliSense sont affichées pour la fonction de routeur ().](../javascript/media/write-code-signature-checking.png)

Vous pouvez également utiliser IntelliSense pour compléter un mot automatiquement quand vous avez tapé suffisamment de caractères pour lever toute ambiguïté sur le mot. Si vous placez votre curseur après la chaîne `data` dans le code suivant et tapez `get`, IntelliSense affiche les fonctions définies plus haut dans le code ou définies dans une bibliothèque tierce que vous avez ajoutée à votre projet.

![Capture d’écran d’une fenêtre de code Visual Studio avec le mot « obtenir » entré. Les informations IntelliSense sont affichées pour toutes les fonctions commençant par « obtenir ».](../javascript/media/write-code-intellisense.png)

IntelliSense peut également afficher des informations sur les types lorsque vous pointez sur les éléments de programmation.

Pour fournir des informations IntelliSense, le service de langage peut utiliser des fichiers *d.ts* TypeScript et des commentaires JSDoc. Pour les bibliothèques JavaScript courantes, les fichiers *d.ts* sont automatiquement acquis. Pour plus d’informations sur la façon dont les informations IntelliSense sont acquises, consultez [JavaScript IntelliSense](../ide/javascript-intellisense.md?toc=/visualstudio/javascript/toc.json)

## <a name="check-syntax"></a>Vérifier la syntaxe

Le service de langage utilise ESLint pour fournir la vérification de la syntaxe et la vérification lint. Si vous avez besoin de définir des options pour la vérification de la syntaxe dans l’éditeur, sélectionnez **Outils**  >  **options**  >  **JavaScript/machine**  >  à inverser. Les options de linting vous dirigent vers le fichier de configuration ESLint général.

Le code suivant illustre la coloration syntaxique en vert (lignes ondulées vertes) sur l’expression. Pointez sur la coloration syntaxique.

![Afficher l’erreur de syntaxe](../javascript/media/write-code-syntax-checking.png)

La dernière ligne de ce message indique que le service de langage attendait une virgule (`,`). La ligne ondulée verte indique un avertissement. La ligne ondulée rouge indique une erreur.

Dans le volet inférieur, vous pouvez cliquer sur l’onglet **Liste d’erreurs** pour afficher l’avertissement et la description, ainsi que le nom de fichier et le numéro de la ligne.

![Afficher la liste des erreurs](../javascript/media/write-code-error-list.png)

Vous pouvez corriger ce code en ajoutant la virgule (`,`) avant `"data"`.

Pour plus d’informations sur les linters, consultez la rubrique sur les [linters](https://github.com/microsoft/JSTSdocs/blob/master/articles/editor/linting.md).

## <a name="comment-out-code"></a>Commenter du code

La barre d’outils, qui est la ligne de boutons sous la barre de menus dans Visual Studio, peut aider à augmenter votre productivité quand vous codez. Par exemple, vous pouvez basculer le mode de complétion IntelliSense ([IntelliSense](../ide/using-intellisense.md) est une aide au codage qui affiche entre autres une liste de méthodes correspondantes), augmenter ou réduire un retrait de ligne, ou commenter du code que vous ne souhaitez pas compiler. Dans cette section, nous allons commenter du code.

Sélectionnez une ou plusieurs lignes de code dans l’éditeur, puis choisissez le bouton **Commenter les lignes sélectionnées**![bouton Commenter](../javascript/media/write-code-comment-out.png) sur la barre d’outils. Si vous préférez utiliser le clavier, appuyez sur **CTRL** + **K**, **CTRL** + **C**.

Les caractères de commentaire JavaScript `//` sont ajoutés au début de chaque ligne sélectionnée pour commenter le code.

## <a name="collapse-code-blocks"></a>Réduire les blocs de code

Si vous avez besoin de clarifier l’affichage de certaines régions de code, vous pouvez le réduire. Choisissez la petite case grise avec le signe moins qui se trouve dans la marge de la première ligne d’une fonction. Ou, si vous êtes un utilisateur du clavier, placez le curseur n’importe où dans le code du constructeur et appuyez sur **CTRL** + **m**, **CTRL** + **m**.

![Bouton de réduction du mode Plan](../javascript/media/write-code-collapse-code.png)

Le bloc de code est réduit de façon à afficher uniquement la première ligne, suivie de points de suspension (`...`). Pour rajouter le bloc de code, cliquez sur la zone grise qui contient maintenant un signe plus (+) ou appuyez de nouveau sur **CTRL** + **m**, **CTRL** + **m** . Cette fonctionnalité, appelée [Mode Plan](../ide/outlining.md), est très utile pour réduire des fonctions longues ou des classes entières.

## <a name="view-definitions"></a>Afficher les définitions

L’éditeur Visual Studio facilite l’inspection de la définition d’un type, d’une fonction, etc. L’une des méthodes consiste à naviguer jusqu’au fichier qui contient la définition, par exemple en choisissant **atteindre la définition** partout où l’élément de programmation est référencé. Une autre façon encore plus rapide, sans avoir à déplacer le focus en dehors du fichier dans lequel vous travaillez, consiste à utiliser la fonctionnalité [Aperçu de la définition](../ide/go-to-and-peek-definition.md#peek-definition). Consultons la définition de la méthode `render` dans l’exemple ci-dessous.

Cliquez avec le bouton droit sur `render`, puis choisissez **Aperçu de la définition** dans le menu de contenu. Ou appuyez sur **ALT** + **F12**.

   Une fenêtre indépendante s’affiche, avec la définition de la méthode `render`. Vous pouvez faire défiler le contenu de la fenêtre indépendante, ou même afficher un aperçu de la définition d’un autre type à partir du code en aperçu.

   ![Fenêtre Aperçu de la définition](../javascript/media/write-code-peek-definition.png)

Fermez la fenêtre Aperçu de la définition en choisissant la petite case avec un « x » dans le coin supérieur droit de la fenêtre indépendante.

## <a name="use-code-snippets"></a>Utiliser des extraits de code

Visual Studio fournit des *extraits de code* qui vous aident à créer rapidement et facilement les blocs de code couramment utilisés. Ces [extraits de code](../ide/code-snippets.md) sont disponibles pour plusieurs langages de programmation, y compris JavaScript. Nous allons ajouter une boucle `for` à votre fichier de code.

Placez le curseur à l’endroit où vous souhaitez insérer l’extrait de code, cliquez avec le bouton droit et choisissez **Snippet**  >  **Insérer** un extrait.

![Extrait de code dans Visual Studio](../javascript/media/write-code-insert-snippet.png)

Une zone **Insérer un extrait de code** s’affiche dans l’éditeur. Choisissez **Général**, puis double-cliquez sur l’élément **for** dans la liste.

![Extrait de code pour une boucle dans Visual Studio](../javascript/media/write-code-insert-snippet-for-loop.png)

Cette opération ajoute l’extrait de code de boucle `for` à votre code :

```javascript
for (var i = 0; i < length; i++) {

}
```

Vous pouvez consulter les extraits de code disponibles pour votre langage en choisissant **modifier** les extraits de code  >  **IntelliSense**  >  , puis en choisissant le dossier de votre langue.

## <a name="see-also"></a>Voir aussi

- [Extraits de code](../ide/code-snippets.md)
- [Naviguer dans le code](../ide/navigating-code.md)
- [mode Plan](../ide/outlining.md)
- [Atteindre la définition et Aperçu de la définition](../ide/go-to-and-peek-definition.md)
- [Refactorisation](../ide/refactoring-in-visual-studio.md)
- [Utilisez IntelliSense](../ide/using-intellisense.md)
