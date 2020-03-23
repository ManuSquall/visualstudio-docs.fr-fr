---
title: Modifier du code R
description: Visual Studio offre une expérience de modification personnalisée pour R, tout en conservant toutes les fonctionnalités et la possibilité d’utiliser des extensions.
ms.date: 11/05/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 7ecfd8f1cf50e94991ce2fd94ad94ac9815c92ca
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302713"
---
# <a name="edit-r-code-in-visual-studio"></a>Modifier le code R dans Visual Studio

Les Outils R pour Visual Studio (RTVS) personnalisent l’expérience de modification dans Visual Studio spécifiquement pour R, tout en conservant toutes les fonctionnalités et la possibilité d’utiliser des extensions. (Par exemple, si vous préférez les combinaisons de touches VIM, vous pouvez installer la version gratuite de l’[extension VsVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim) à partir de la Place de marché Visual Studio.)

Outre les fonctionnalités décrites dans cet article, consultez également [IntelliSense](r-intellisense.md), [Linting](linting-r-code.md), [Extraits de code](code-snippets-for-r.md) et [R Markdown](rmarkdown-with-r-in-visual-studio.md).

## <a name="syntax-highlighting"></a>Mise en surbrillance de la syntaxe

En plus de colorer différentes parties de votre code, comme les chaînes, les commentaires et les mots clés, RTVS met en évidence et active des liens dans les commentaires :

![Couleurs de syntaxe pour le code R](media/editing-syntax-colors.png)

Pour personnaliser les polices et certaines couleurs de surbrillance, sélectionnez la commande **Tools** > **Options,** naviguez vers **Environment** > **Fonts and Colors,** puis modifiez les paramètres pour les éléments liés à la R dans la boîte **d’éléments d’affichage** :

![Polices et options de couleur pour le code R](media/editing-syntax-colors-options.png)

Visual Studio souligne également les erreurs de syntaxe dans l’éditeur :

![Mise en surbrillance des erreurs de syntaxe dans le code R](media/editing-syntax-error.png)

Pour changer ce comportement, consultez le paramètre de**vérification Syntaxe** **avancée** > sous les options [de l’éditeur](#editor-options).

## <a name="edit-and-organize-code"></a>Modifier et organiser le code

Quand vous tapez du code, RTVS propose une saisie semi-automatique, comme décrit dans la page [IntelliSense](r-intellisense.md). Il applique également une mise en forme automatique comme la saisie semi-automatique des parenthèses et des accolades :

![Animation de la mise en forme inline](media/editing-inline-formatting.gif)

Quand vous tapez des appels à des fonctions qui ont plusieurs paramètres, souvent, vous voulez organiser les paramètres pour rendre le code plus facile à lire. RTVS se souvient du retrait que vous avez défini pour les paramètres et applique automatiquement ce retrait aux lignes suivantes :

![Animation du retrait automatique](media/editing-auto-indentation.gif)

Pour changer ce comportement, consultez les [options de l’éditeur](#editor-options) pour le groupe **Onglets**.

Les régions de code réductibles vous permettent de masquer temporairement une partie de code dans l’éditeur. Visual Studio crée automatiquement différentes régions pour vous, comme pour les relevés multi-lignes, à moins que l’option**Outlining** > **d’exposé** du Code **d’exposé avancé** > ne soit définie.

Pour créer une région de votre choix, entourez le code souhaité avec des commentaires qui se terminent par `---`. Les contrôles +/- à gauche du code vous permettent ensuite de développer et réduire des régions :

![Création d’une zone réductible avec des commentaires](media/editing-collapsible-regions.gif)

Par défaut, Visual Studio insère des espaces lorsque vous appuyez sur la touche **Tab.** Vous pouvez là encore modifier ce comportement, comme décrit dans [Options, Éditeur de texte, Onglets](../ide/reference/options-text-editor-all-languages.md).

## <a name="code-navigation"></a>Navigation dans le code

La navigation dans le code vous permet d’accéder rapidement au code source de votre programme R et à ses bibliothèques. Ces fonctionnalités vous permettent de rester concentré sur votre travail, plutôt que d’avoir à rechercher le code manuellement.

La fonctionnalité **Atteindre la définition** permet d’accéder rapidement à une définition de fonction ou affiche un mini-éditeur inline pour lire le code source d’une fonction de bibliothèque. Il suffit de cliquer à droite sur la fonction d’intérêt et de sélectionner **Go To Definition**, ou placez le curseur dans la fonction et appuyez sur **F12**.

Cette commande ouvre une nouvelle fenêtre d’éditeur contenant le code source de la fonction. Le curseur est positionné de façon pratique au début de la définition de fonction.

**Peek Definition**, invoqué à partir du menu à clic droit ou **Alt**+**F12**, insère une région lisible et défilementable contenant le code source de la fonction ci-dessous l’appel de fonction :

![Animation de l’aperçu de la définition](media/editing-peek-definition.gif)

## <a name="send-code-to-the-interactive-window"></a>Envoyer du code dans la fenêtre interactive

De nombreux développeurs aiment écrire du code dans l’éditeur, puis l’envoyer dans la [fenêtre interactive](interactive-repl-for-r-in-visual-studio.md) pour le tester immédiatement (il s’agit de la boucle REPL : read-evaluate-print loop). Appuyer **sur Ctrl**+**Enter** dans l’éditeur R envoie la ligne de code actuelle à la fenêtre interactive, puis place le curseur sur la ligne suivante. Avec **Ctrl**+**Enter**, alors, vous pouvez effectivement passer à travers votre code à partir de l’éditeur.

Vous pouvez également sélectionner le code et appuyer sur **Ctrl**+**Enter** pour appliquer toute cette sélection. Sinon, cliquez avec le bouton droit sur la sélection et sélectionnez **Exécuter en mode interactif**.

## <a name="format-code"></a>Code du format

La mise en forme automatique de Visual Studio conserve la mise en forme du code que vous écrivez, ainsi que celle du code que vous collez dans l’éditeur, conformément à vos préférences. Vous pouvez également faire une sélection, clic droit, et sélectionner **La sélection de format** (**Ctrl**+**K**,**F**) pour appliquer ces préférences. Par exemple, si vous avez une définition de fonction tenant sur une seule ligne :

```R
f<-function  (a){  return(a + 1) }
```

L’application de la mise en forme la transforme en ce qui suit :

```R
f <- function(a) { return(a + 1) }
```

Pour reformer l’ensemble du fichier de code, sélectionnez **Edit** > **Advanced** > **Format Document** (**Ctrl**+**E**,**D**).

La mise en forme automatique est une opération distincte qui peut être annulée. Par exemple, si vous collez du code dans l’éditeur et que vous le formatez s’applique, la+sélection **d’Edit** > **Undo** ou le pressage **de Ctrl****Z** une fois inverse le formatage ; un deuxième **Annuler** inverse la pâte elle-même.

Les options de formatage (y compris l’arrêt du formatage) sont définies par **des options d’outils** > **Options** sur l’onglet**R** > **Advanced** **de l’éditeur** > de texte. Vous pouvez vous rendre directement sur cette page en utilisant la commande**d’options** **R Tools** > Editor ou en cliquant à droite dans l’éditeur et en sélectionnant les **options de formatage**. Consultez la section des [options de l’éditeur](#editor-options) pour plus d’informations.

## <a name="inserting-roxygen-comments"></a>Insertion de commentaires Roxygen

RTVS fournit un raccourci pour la génération de commentaires [Roxygen](https://cran.r-project.org/web/packages/roxygen2/index.html) à l’aide des noms de paramètre d’une fonction. Il suffit de taper `###` sur une ligne vide au-dessus de la définition de fonction :

![Animation de l’insertion d’un commentaire Roxygen](media/editing-roxygen-comments.gif)

## <a name="editor-options"></a>Options de l’éditeur

Les options spécifiques à l’éditeur sont définies par la commande **Tools** > **Options,** naviguant vers **Text Editor** > **R**, ou utilisez la commande de raccourci R **Tools** > **Editor Options**.

Les options des onglets **Général**, **Barres de défilement** et **Onglets** ne sont pas propres à R, mais sont plutôt des paramètres généraux de Visual Studio disponibles pour tous les langages, mais appliqués langage par langage. Pour plus de détails, consultez les articles suivants :

- [Options, Éditeur de texte, Tous les langages](../ide/reference/options-text-editor-all-languages.md)
- [Suivre votre code en personnalisant la barre de défilement](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)
- [Options, Éditeur de texte, Onglets](../ide/reference/options-text-editor-all-languages-tabs.md)

Les options sur l’onglet **R** > **Advanced** sont spécifiques à RTVS :

| Groupe | Option | Default | Description |
| --- | --- | --- | --- |
| Mise en forme | Mise en forme automatique | Il en va | Remet en forme le code à mesure que vous tapez. N’affecte pas les commandes **Mettre la sélection en forme** ou **Mettre le document en forme**. |
| | Accolades développées | Off | Place une { ouvrante sur une nouvelle ligne. |
| | Mettre en forme lors du collage | Il en va | Applique la mise en forme lors du collage. |
| | Mettre en forme la portée après } | Il en va | Met en forme la portée après avoir tapé une } fermante. |
| | Espace après une virgule | Il en va | Place un espace après les virgules. |
| | Espace après un mot clé | Il en va | Insère un espace après les mots clés comme `if`, `while` et `repeat`. |
| | Espace avant { | Il en va | Place un espace avant une { ouvrante. |
| | Espace autour de = | Il en va | Place des espaces autour d’un signe égal. |
| IntelliSense | Valider après la touche Entrée | Off | Engage la sélection d’auto-achèvement lorsque **Enter** est pressé. |
| | Valider après la touche Espace | Off | Engage la sélection d’auto-achèvement lorsque **l’espace** est pressé.|
| | Liste de saisie semi-automatique après le premier caractère | Il en va | Affiche la liste de saisie semi-automatique quand vous tapez les premiers caractères. Lorsqu’il est éteint, une liste d’achèvement est affichée avec **Edit** > **IntelliSense** > **List Members** (**Ctrl**+**J**). |
| | Liste d’achèvement sur la clé **de l’onglet** | Off | Invoque la liste d’achèvement en tapant un ou plusieurs caractères et en appuyant sur **Tab**. |
| | Correspondance partielle de noms d’argument de types | Off | Quand vous tapez des noms d’argument dans un appel de fonction, l’aide de la signature affiche une description de l’argument qui correspond le mieux. |
| Fenêtre interactive | Vérification syntaxique dans la console R | Off | Applique la vérification syntaxique dans la fenêtre interactive. La vérification syntaxique peut ne pas fonctionner correctement avec les instructions multilignes. |
| Mode Plan | Plan du code | Il en va | Crée automatiquement des régions réductibles pour des zones comme les instructions multilignes. |
| Vérification syntaxique | Afficher les erreurs de syntaxe | Il en va | Active la vérification syntaxique automatique du code. |
