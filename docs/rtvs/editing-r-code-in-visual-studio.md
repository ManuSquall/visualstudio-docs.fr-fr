---
title: Modification de code avec les Outils R pour Visual Studio | Microsoft Docs
description: "Visual Studio offre une expérience de modification personnalisée pour R, tout en conservant toutes les fonctionnalités et la possibilité d’utiliser des extensions."
ms.custom: 
ms.date: 01/24/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: 2650d366cd174b9964142b76048cda6e4b3c3497
ms.sourcegitcommit: ba29e4d37db92ec784d4acf9c6e120cf0ea677e9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2018
---
# <a name="editing-r-code-in-visual-studio"></a>Modification de code R dans Visual Studio

Les Outils R pour Visual Studio (RTVS) personnalisent l’expérience de modification dans Visual Studio spécifiquement pour R, tout en conservant toutes les fonctionnalités et la possibilité d’utiliser des extensions. (Par exemple, si vous préférez les combinaisons de touches VIM, vous pouvez installer la version gratuite de l’[extension VsVim](https://visualstudiogallery.msdn.microsoft.com/59ca71b3-a4a3-46ca-8fe1-0e90e3f79329) à partir de la galerie Visual Studio.)

Outre les fonctionnalités décrites dans cet article, consultez également [IntelliSense](r-intellisense.md), [Linting](linting-r-code.md), [Extraits de code](code-snippets-for-r.md) et [R Markdown](rmarkdown-with-r-in-visual-studio.md).

## <a name="syntax-highlighting"></a>Mise en surbrillance de la syntaxe

En plus de colorer différentes parties de votre code, comme les chaînes, les commentaires et les mots clés, RTVS met en évidence et active des liens dans les commentaires :

![Couleurs de syntaxe pour le code R](media/editing-syntax-colors.png)

Pour personnaliser les polices et certaines couleurs de surbrillance, sélectionnez la commande **Outils > Options**, accédez à **Environnement > Polices et couleurs**, puis modifiez les paramètres pour les éléments liés à R dans la zone **Éléments affichés :** :

![Polices et options de couleur pour le code R](media/editing-syntax-colors-options.png)

Visual Studio souligne également les erreurs de syntaxe dans l’éditeur :

![Mise en surbrillance des erreurs de syntaxe dans le code R](media/editing-syntax-error.png)

Pour changer ce comportement, consultez le paramètre **Avancé > Vérification de la syntaxe** sous [Options de l’éditeur](#editor-options).

## <a name="editing-and-organizing-code"></a>Modification et organisation du code

Quand vous tapez du code, RTVS propose une saisie semi-automatique, comme décrit dans la page [IntelliSense](r-intellisense.md). Il applique également une mise en forme automatique comme la saisie semi-automatique des parenthèses et des accolades : 

![Animation de la mise en forme inline](media/editing-inline-formatting.gif)

Quand vous tapez des appels à des fonctions qui ont plusieurs paramètres, souvent, vous voulez organiser les paramètres pour rendre le code plus facile à lire. RTVS se souvient du retrait que vous avez défini pour les paramètres et applique automatiquement ce retrait aux lignes suivantes :

![Animation du retrait automatique](media/editing-auto-indentation.gif)

Pour changer ce comportement, consultez les [options de l’éditeur](#editor-options) pour le groupe **Onglets**.

Les régions de code réductibles vous permettent de masquer temporairement une partie de code dans l’éditeur. Visual Studio crée différentes régions automatiquement pour vous, comme pour les instructions multilignes, sauf si l’option **Avancé > Mode plan > Plan du code** est désactivée.

Pour créer une région de votre choix, entourez le code souhaité avec des commentaires qui se terminent par `---`. Les contrôles +/- à gauche du code vous permettent ensuite de développer et réduire des régions :

![Création d’une zone réductible avec des commentaires](media/editing-collapsible-regions.gif)

Par défaut, Visual Studio insère des espaces quand vous appuyez sur la touche Tab. Vous pouvez là encore modifier ce comportement, comme décrit dans [Options, Éditeur de texte, Onglets](../ide/reference/options-text-editor-all-languages.md).

## <a name="code-navigation"></a>Navigation dans le code

La navigation dans le code vous permet d’accéder rapidement au code source de votre programme R et à ses bibliothèques. Ces fonctionnalités vous permettent de rester concentré sur votre travail, plutôt que d’avoir à rechercher le code manuellement.

La fonctionnalité **Atteindre la définition** permet d’accéder rapidement à une définition de fonction ou affiche un mini-éditeur inline pour lire le code source d’une fonction de bibliothèque. Cliquez simplement avec le bouton droit sur la fonction qui vous intéresse et sélectionnez **Atteindre la définition**, ou placez le curseur dans la fonction et appuyez sur F12.

Cette commande ouvre une nouvelle fenêtre d’éditeur contenant le code source de la fonction. Le curseur est positionné de façon pratique au début de la définition de fonction.

La fonctionnalité **Aperçu de la définition**, appelée à partir du menu contextuel ou en appuyant sur Alt+F12, insère une zone de défilement en lecture seule qui contient le code source de la fonction située en dessous de l’appel de fonction :

![Animation de l’aperçu de la définition](media/editing-peek-definition.gif)

## <a name="sending-code-to-the-interactive-window"></a>Envoi de code dans la fenêtre interactive

De nombreux développeurs aiment écrire du code dans l’éditeur, puis l’envoyer dans la [fenêtre interactive](interactive-repl-for-r-in-visual-studio.md) pour le tester immédiatement (il s’agit de la boucle REPL : read-evaluate-print loop). En appuyant sur Ctrl+Entrée dans l’éditeur R, vous envoyez la ligne de code actuelle à la fenêtre interactive, puis placez le curseur sur la ligne suivante. En appuyant sur Ctrl+Entrée, donc, vous pouvez efficacement parcourir votre code à partir de l’éditeur.

Vous pouvez également sélectionner du code et appuyer sur Ctrl+Entrée pour appliquer toute cette sélection. Sinon, cliquez avec le bouton droit sur la sélection et sélectionnez **Exécuter en mode interactif**.

## <a name="formatting-code"></a>Mise en forme du code

La mise en forme automatique de Visual Studio conserve la mise en forme du code que vous écrivez, ainsi que celle du code que vous collez dans l’éditeur, conformément à vos préférences. Vous pouvez également effectuer une sélection, cliquer avec le bouton droit, puis sélectionner **Mettre la sélection en forme** (Ctrl+K,F) pour appliquer ces préférences. Par exemple, si vous avez une définition de fonction tenant sur une seule ligne :

```R
f<-function  (a){  return(a + 1) }
```

L’application de la mise en forme la transforme en ce qui suit :

```R
f <- function(a) { return(a + 1) }
```

Pour remettre en forme la totalité du fichier de code, sélectionnez **Modifier > Avancé > Mettre le document en forme** (Ctrl+E,D).

La mise en forme automatique est une opération distincte qui peut être annulée. Par exemple, si vous collez du code dans l’éditeur et que la mise en forme s’applique, en sélectionnant **Modifier > Annuler** ou en appuyant sur Ctrl+Z une fois, vous inversez la mise en forme. Une deuxième annulation inverse le collage lui-même.

Les options de mise en forme (dont la désactivation de la mise en forme) sont définies dans **Outils > Options** sous l’onglet **Éditeur de texte > R > Avancé**. Vous pouvez accéder directement à cette page à l’aide la commande **Outils R > Options de l’éditeur...** ou en cliquant avec le bouton droit dans l’éditeur et en sélectionnant **Options de mise en forme...**. Consultez la section des [options de l’éditeur](#editor-options) pour plus d’informations.

## <a name="inserting-roxygen-comments"></a>Insertion de commentaires Roxygen

RTVS fournit un raccourci pour la génération de commentaires [Roxygen](http://roxygen.org/) à l’aide des noms de paramètre d’une fonction. Il suffit de taper `###` sur une ligne vide au-dessus de la définition de fonction :

![Animation de l’insertion d’un commentaire Roxygen](media/editing-roxygen-comments.gif)

## <a name="editor-options"></a>Options de l’éditeur

Les options spécifiques de l’éditeur sont définies par la commande **Outils > Options**, en accédant à **Éditeur de texte > R**, ou en utilisant la commande de raccourci **Outils R > Options de l’éditeur...**.

Les options des onglets **Général**, **Barres de défilement** et **Onglets** ne sont pas propres à R, mais sont plutôt des paramètres généraux de Visual Studio disponibles pour tous les langages, mais appliqués langage par langage. Pour plus d’informations, consultez les articles suivants :

- [Options, Éditeur de texte, Tous les langages](../ide/reference/options-text-editor-all-languages.md)
- [Suivre votre code en personnalisant la barre de défilement](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)
- [Options, Éditeur de texte, Onglets](../ide/reference/options-text-editor-all-languages-tabs.md)

Les options de l’onglet **R > Avancé** sont propres à RTVS :

| Regrouper | Option | Par défaut | Description |
| --- | --- | --- | --- |
| Mise en forme | Mise en forme automatique | Activé | Remet en forme le code à mesure que vous tapez. N’affecte pas les commandes **Mettre la sélection en forme** ou **Mettre le document en forme**. |
| | Accolades développées | Off | Place une { ouvrante sur une nouvelle ligne. |
| | Mettre en forme lors du collage | Activé | Applique la mise en forme lors du collage. |
| | Mettre en forme la portée après } | Activé | Met en forme la portée après avoir tapé une } fermante. |
| | Espace après une virgule | Activé | Place un espace après les virgules. |
| | Espace après un mot clé | Activé | Insère un espace après les mots clés comme `if`, `while` et `repeat`. |
| | Espace avant { | Activé | Place un espace avant une { ouvrante. |
| | Espace autour de = | Activé | Place des espaces autour d’un signe égal. |
| IntelliSense | Valider après la touche Entrée | Off | Valide la sélection de saisie semi-automatique quand vous appuyez sur Entrée. |
| | Valider après la touche Espace | Off | Valide la sélection de saisie semi-automatique quand vous appuyez sur Espace.|
| | Liste de saisie semi-automatique après le premier caractère | Activé | Affiche la liste de saisie semi-automatique quand vous tapez les premiers caractères. Si elle est désactivée, vous affichez la liste de saisie semi-automatique avec **Modifier > IntelliSense > Liste des membres** (Ctrl+J). |
| | Liste de saisie semi-automatique quand la touche Tab est enfoncée | Off | Appelle la liste de saisie semi-automatique en tapant un ou plusieurs caractères et en appuyant sur Tab. |
| | Correspondance partielle de noms d’argument de types | Off | Quand vous tapez des noms d’argument dans un appel de fonction, l’aide de la signature affiche une description de l’argument qui correspond le mieux. |
| Fenêtre interactive | Vérification syntaxique dans la console R | Off | Applique la vérification syntaxique dans la fenêtre interactive. La vérification syntaxique peut ne pas fonctionner correctement avec les instructions multilignes. | 
| mode Plan | Plan du code | Activé | Crée automatiquement des régions réductibles pour des zones comme les instructions multilignes. |
| Vérification syntaxique | Afficher les erreurs de syntaxe | Activé | Active la vérification syntaxique automatique du code. |
