---
title: "IntelliSense pour le code R Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 4/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d96e3677-e5ec-4e11-82a8-d914a93b1aa9
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 359b9dc6bae84bb6d89e5f0f646c0b8fed5898ec
ms.contentlocale: fr-fr
ms.lasthandoff: 05/12/2017

---


# <a name="intellisense"></a>IntelliSense

La fonctionnalité IntelliSense de Visual Studio affiche des informations sur les fonctions que vous pouvez appeler, les membres des objets, les arguments de fonction et les [extraits de code](code-snippets.md) directement dans votre champ de vision à mesure que vous écrivez du code. Elle affiche également les saisies semi-automatiques possibles à mesure que vous tapez, et applique la saisie semi-automatique quand vous appuyez sur les touches Tab ou Entrée (consultez les [options de l’éditeur](code-editing.md#editor-options) pour l’onglet **Avancé**). La fonctionnalité IntelliSense est disponible à la fois dans l’éditeur et dans la [fenêtre interactive](interactive-repl.md).

![IntelliSense affichant une signature de fonction](~/docs/rtvs/media/intellisense-function-signature.png) 

Quand vous tapez une fonction ou une autre instruction, IntelliSense fournit un menu de saisie semi-automatique filtrée (sensible à la casse) d’après ce que vous avez déjà tapé :

![Menu de saisie semi-automatique IntelliSense](~/docs/rtvs/media/intellisense-auto-complete-menu.png)

Quand vous appuyez sur Tab (ou Entrée ou Espace, selon la façon dont les options sont définies), l’élément sélectionné de la liste déroulante est inséré. Vous pouvez changer la sélection avec les touches de direction. 

IntelliSense fournit également des suggestions pour les membres des objets R :
 
![Suggestions IntelliSense pour les membres d’objet](~/docs/rtvs/media/intellisense-auto-complete-r-objects.png)
 
Appuyez sur ÉCHAP pour fermer le menu. Vous pouvez le rappeler en appuyant sur Ctrl+Espace.

Le fait de taper la parenthèse ouvrante `(` pour un appel de fonction insère la parenthèse fermante `)` et affiche l’aide de la signature comme indiqué plus haut :

![Aide de la signature IntelliSense pour une fonction](~/docs/rtvs/media/intellisense-function-signature.png)

Là encore, la touche ÉCHAP permet de fermer la fenêtre contextuelle. Pour les signatures de fonction, vous pouvez la rappeler avec Ctrl+Maj+Espace.

> [!Tip]
> Si vous trouvez que l’aide du paramètre dissimule le texte situé en dessous, comme ce peut être le cas dans l’éditeur de fichiers, vous pouvez appuyer de façon prolongée sur la touche Ctrl pour rendre translucide le texte d’aide du paramètre.

## <a name="intellisense-for-user-defined-functions-and-variables"></a>IntelliSense pour les fonctions définies par l’utilisateur et les variables

IntelliSense s’appliquent aux fonctions définies par l’utilisateur dans le même fichier, y compris la saisie semi-automatique des paramètres de nom :

![IntelliSense pour les fonctions définies par l’utilisateur](~/docs/rtvs/media/intellisense-same-file-functions.png)

![Saisie semi-automatique IntelliSense de paramètres pour les fonctions définies par l’utilisateur](~/docs/rtvs/media/intellisense-parameter-completion.png)

IntelliSense s’applique également aux variables dans le même fichier et la session actuelle :

![Saisie semi-automatique IntelliSense de variables](~/docs/rtvs/media/intellisense-variable-completion.png)

> [!Note]
> Dans la fenêtre interactive, IntelliSense prend en compte uniquement les noms dans la session R actuelle et ignore les fichiers de votre projet.

## <a name="code-suggestions"></a>Suggestions de code

Quand une ampoule (appelée balise active) apparaît dans la marge, Visual Studio suggère qu’un raccourci est disponible pour une action couramment utilisée. Par exemple, si vous placez le curseur sur une ligne contenant une instruction `library` dans l’éditeur, une ampoule s’affiche. Sélectionnez l’ampoule pour afficher les options disponibles :

![Balises actives pour R dans l’éditeur](~/docs/rtvs/media/intellisense-smart-tags.png)

