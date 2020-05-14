---
title: Refactorisation du code
description: Affinage du code avec Visual Studio pour Mac et des actions rapides.
author: cobey
ms.author: cobey
ms.date: 03/29/2019
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 5a87b87f3a14462daec1e069fe222164818d2a19
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "67691298"
---
# <a name="refactoring"></a>Refactorisation

La refactorisation du code consiste à réorganiser, restructurer et clarifier le code existant tout en garantissant que le comportement global du code ne change pas.

Elle génère une base de code plus saine, rendant le code plus utilisable, lisible et gérable pour vous ou pour tout autre développeur ou utilisateur susceptible de faire référence au code.

L’intégration de Visual Studio pour Mac à Roslyn, la plateforme de compilateurs .NET open source de Microsoft, permet une refactorisation plus importante.

## <a name="renaming"></a>Renommage

La commande de refactorisation *Renommer* peut être utilisée sur n’importe quel identificateur du code (par exemple un nom de classe, un nom de propriété, etc.) pour rechercher toutes les occurrences de cet identificateur et les changer. Pour renommer un symbole, cliquez dessus avec le bouton droit, puis choisissez **Renommer...**, ou utilisez la combinaison de touches **Cmd (⌘) + R** :

![Élément de menu Renommer](media/refactoring-renaming1.png)

Ceci met en évidence le symbole et toutes les références à celui-ci. Quand vous commencez à taper un nouveau nom, il change automatiquement toutes les références figurant dans votre code. Vous pouvez valider vos changements en appuyant sur **Entrée** :

![Renommage et identificateur](media/refactoring-renaming2.png)

## <a name="quick-actions"></a>Actions rapides

Les actions rapides vous permettent de refactoriser, générer ou modifier facilement le code en une seule action.

Les actions rapides peuvent servir à :

* Appliquer un correctif de code en cas de violation de règle de l’analyseur de code
* Supprimer une violation de règle de l’analyseur de code
* Appliquer une refactorisation (par exemple, rendre inline une variable temporaire)
* Générer du code (par exemple, introduire une variable locale)

Actions rapides peuvent être appliquées ![en](media/quick-actions-light-bulb-icon.png) utilisant l’icône de](media/quick-actions-screwdriver-icon.png) l’ampoule ou des icônes d’icônes de tournevis tournevis, ![ou en appuyant sur **Option ()**+**Entrez** lorsque votre curseur est sur une ligne de code pour laquelle une action est disponible. Vous voyez une ampoule d’erreur ![icône en forme d’ampoule d’erreur](media/quick-actions-error-light-bulb-icon.png) s’il existe une ligne ondulée rouge indiquant une erreur, pour laquelle Visual Studio met à disposition un correctif.

Des éditeurs tiers peuvent fournir des diagnostics et des suggestions personnalisés pour n’importe quel langage, par exemple dans le cadre d’un Kit de développement logiciel (SDK). Dans ce cas, les ampoules Visual Studio s’allument en fonction des règles établies.

### <a name="quick-action-icons"></a>Icônes d’actions rapides
L’icône qui s’affiche quand une action rapide est disponible donne une indication du type de correctif ou de refactorisation disponible. L’icône en forme de *tournevis* ![icône en forme de tournevis](media/quick-actions-screwdriver-icon.png) indique simplement que des actions sont disponibles pour modifier le code, mais vous ne devez pas nécessairement les utiliser. L’icône en forme *d’ampoule jaune* ![icône en forme d’ampoule](media/quick-actions-light-bulb-icon.png) indique qu’il existe des actions disponibles que vous *devez* effectuer pour améliorer votre code. L’icône en forme *d’ampoule d’erreur* ![icône en forme d’ampoule d’erreur](media/quick-actions-error-light-bulb-icon.png) indique qu’une action est disponible pour résoudre une erreur dans votre code.

### <a name="to-see-a-light-bulb-or-screwdriver"></a>Pour afficher une ampoule ou un tournevis

- Si un correctif est disponible, les ampoules apparaissent spontanément quand vous placez le pointeur de la souris à l’emplacement d’une erreur.

   ![Ampoule avec pointage de la souris](media/refactoring-lightbulb-hover.png)

- Les ampoules et tournevis apparaissent dans la marge de gauche de l’éditeur quand vous déplacez le signe insertion dans une ligne de code pour lequel une action rapide est disponible.

- Option de presse ()+**Entrez** **n’importe**où sur une ligne pour voir une liste d’actions rapides et de refactorations disponibles.

![Afficher les éléments contextuels](media/refactoring-context-action.png)

En passant le pointeur de la souris sur les actions contextuelles, vous obtenez un aperçu de ce qui est ajouté ou supprimé dans votre code.

![Option Entrer les éléments contextuels](media/refactoring-image2a.png)

Pour activer ces options, vous devez sélectionner *Activer l’analyse du code source des fichiers ouverts* dans les options de **Visual Studio pour Mac > Préférences > Éditeur de texte > Analyse du code source** :

![Activer l’analyse du code source](media/refactoring-options.png)

Il existe plus de 100 actions possibles qui peuvent être suggérées, qui sont activées ou désactivées en accédant à **Visual Studio pour Mac > Préférences > Analyse du code source > C# > Actions de code**, et en cochant ou en décochant la case en regard de l’action :

![Actions de l’analyse du code source C#](media/refactoring-image3a.png)

### <a name="common-quick-actions"></a>Actions rapides courantes

Vous pouvez en apprendre plus sur les actions rapides courantes dans l’article [Actions rapides courantes](/visualstudio/ide/common-quick-actions).

## <a name="source-analysis"></a>Analyse du code source

L’analyse du code source analyse votre code à la volée. Elle souligne les erreurs potentielles et les violations de style, et fournit des corrections automatiques sous forme d’actions contextuelles.

Vous pouvez voir tous les résultats de l’analyse du code source pour n’importe quel fichier et à tout moment, en consultant la barre de défilement sur le côté droit de l’éditeur de texte :

![Barre latérale Analyse du code source](media/refactoring-image4a.png)

Si vous cliquez sur le cercle en haut, vous pouvez parcourir les différentes suggestions, les problèmes avec la gravité la plus élevée figurant en premier. Passez le pointeur sur un résultat ou une ligne individuelle pour afficher le problème. Vous pouvez alors le corriger via des actions contextuelles :

![Élément d’analyse du code source](media/refactoring-image5.png)

## <a name="related-video"></a>Vidéo associée

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Refactoring-Code/player]

## <a name="see-also"></a>Voir aussi

- [Actions rapides (Visual Studio sur Windows)](/visualstudio/ide/quick-actions)
- [Refactoriser du code (Visual Studio sur Windows)](/visualstudio/ide/refactoring-in-visual-studio)