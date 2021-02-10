---
title: IntelliSense pour le code R
description: Visual Studio IntelliSense affiche des informations sur les fonctions, les membres d’objet, les extraits de code et les saisies semi-automatiques au fur et à mesure que vous tapez du code R.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: de6a8ffbaa0fb10929d013a351ebffa8e3f4b529
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939433"
---
# <a name="intellisense"></a>IntelliSense

La fonctionnalité IntelliSense de Visual Studio affiche des informations sur les fonctions que vous pouvez appeler, les membres des objets, les arguments de fonction et les [extraits de code](code-snippets-for-r.md) directement dans votre champ de vision à mesure que vous écrivez du code. Il affiche également les saisies semi-automatiques possibles au fur et à mesure que vous tapez, et se termine lorsque vous appuyez sur l' **onglet** ou **Entrez** des touches (consultez Options de l' [éditeur](editing-r-code-in-visual-studio.md#editor-options) pour l’onglet **avancé** ). La fonctionnalité IntelliSense est disponible à la fois dans l’éditeur et dans la [fenêtre interactive](interactive-repl-for-r-in-visual-studio.md).

![IntelliSense affichant une signature de fonction](media/intellisense-function-signature.png)

Quand vous tapez une fonction ou une autre instruction, IntelliSense fournit un menu de saisie semi-automatique filtrée (sensible à la casse) d’après ce que vous avez déjà tapé :

![Menu de saisie semi-automatique IntelliSense](media/intellisense-auto-complete-menu.png)

En appuyant sur la touche **Tab** (ou **entrée**, ou **espace**, selon la façon dont les options sont définies), insère l’élément sélectionné dans la liste déroulante. Vous pouvez changer la sélection avec les touches de direction.

IntelliSense fournit également des suggestions pour les membres des objets R :

![Suggestions IntelliSense pour les membres d’objet](media/intellisense-auto-complete-r-objects.png)

Appuyez sur **Échap** pour fermer complètement le menu. Vous pouvez le rétablir avec l’espace **CTRL** + .

Le fait de taper la parenthèse ouvrante `(` pour un appel de fonction insère la parenthèse fermante `)` et affiche l’aide de la signature comme indiqué plus haut :

![Aide de la signature IntelliSense pour une fonction](media/intellisense-function-signature.png)

Là encore, la **touche Échap** ferme la fenêtre contextuelle. pour les signatures de fonction, vous pouvez la refaire avec **CTRL** + **+** + **espace**.

> [!Tip]
> Si le paramètre aide obscurcit le texte situé en dessous, appuyez sur la touche **CTRL** et maintenez-la enfoncée pour rendre translucide le texte d’aide du paramètre.

## <a name="intellisense-for-user-defined-functions-and-variables"></a>IntelliSense pour les fonctions définies par l’utilisateur et les variables

IntelliSense s’appliquent aux fonctions définies par l’utilisateur dans le même fichier, y compris la saisie semi-automatique des paramètres de nom :

![IntelliSense pour les fonctions définies par l’utilisateur](media/intellisense-same-file-functions.png)

![Saisie semi-automatique IntelliSense de paramètres pour les fonctions définies par l’utilisateur](media/intellisense-parameter-completion.png)

IntelliSense s’applique également aux variables dans le même fichier et la session actuelle :

![Saisie semi-automatique IntelliSense de variables](media/intellisense-variable-completion.png)

> [!Note]
> Dans la fenêtre interactive, IntelliSense prend en compte uniquement les noms dans la session R actuelle et ignore les fichiers de votre projet.

## <a name="code-suggestions"></a>Suggestions de code

Quand une ampoule (appelée balise active) apparaît dans la marge, Visual Studio suggère qu’un raccourci est disponible pour une action couramment utilisée. Par exemple, placez le curseur sur une ligne contenant une instruction `library` dans l’éditeur pour afficher une ampoule. Sélectionnez l’ampoule pour afficher les options disponibles :

![Balises actives pour R dans l’éditeur](media/intellisense-smart-tags.png)
