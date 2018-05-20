---
title: Actions rapides, ampoules et tournevis
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d413d5b440c39c3603e1e909fb0c4645719f188b
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2018
---
# <a name="quick-actions"></a>Actions rapides

Les actions rapides vous permettent de refactoriser, générer ou modifier facilement le code en une seule action. Les actions rapides sont disponibles pour les fichiers C#, [C++](/cpp/ide/writing-and-refactoring-code-cpp) et Visual Basic. Certaines actions sont spécifiques à un langage, d’autres s’appliquent à tous les langages.

Les actions rapides peuvent servir à :

- appliquer un correctif de code en cas de violation de règle de [l’analyseur de code](../code-quality/roslyn-analyzers-overview.md) ;
- [supprimer](../code-quality/use-roslyn-analyzers.md) une violation de règle de l’analyseur de code ;
- appliquer une refactorisation (par exemple, [rendre inline une variable temporaire](../ide/reference/inline-temporary-variable.md)) ;
- générer du code (par exemple, [introduire une variable locale](../ide/reference/introduce-local-variable.md)).

Les actions rapides peuvent être appliquées en utilisant l’icône en forme d’ampoule ![icône en forme d’ampoule](media/light-bulb-icon.png) ou de tournevis ![icône en forme de tournevis](media/screwdriver-icon.png), ou en appuyant sur **Ctrl**+**.** lorsque le curseur se trouve sur une ligne de code pour laquelle une action est disponible. Vous voyez une ampoule d’erreur ![icône en forme d’ampoule d’erreur](media/error-light-bulb-icon.png) s’il existe une ligne ondulée rouge indiquant une erreur, pour laquelle Visual Studio met à disposition un correctif.

Des éditeurs tiers peuvent fournir des diagnostics et des suggestions personnalisés pour n’importe quel langage, par exemple dans le cadre d’un Kit de développement logiciel (SDK). Dans ce cas, les ampoules Visual Studio s’allument en fonction des règles établies.

## <a name="icons"></a>Icônes

L’icône qui s’affiche quand une action rapide est disponible donne une indication du type de correctif ou de refactorisation disponible. L’icône en forme de *tournevis* ![icône en forme de tournevis](media/screwdriver-icon.png) indique simplement que des actions sont disponibles pour modifier le code, mais vous ne devez pas nécessairement les utiliser. L’icône en forme *d’ampoule jaune* ![icône en forme d’ampoule](media/light-bulb-icon.png) indique qu’il existe des actions disponibles que vous *devez* effectuer pour améliorer votre code. L’icône en forme *d’ampoule d’erreur* ![icône en forme d’ampoule d’erreur](media/error-light-bulb-icon.png) indique qu’une action est disponible pour résoudre une erreur dans votre code.

## <a name="to-see-a-light-bulb-or-screwdriver"></a>Pour afficher une ampoule ou un tournevis

- Si un correctif est disponible, les ampoules apparaissent spontanément quand vous placez le pointeur de la souris à l’emplacement d’une erreur.

   ![Ampoule avec pointage de la souris](../ide/media/vs2015_lightbulb_hover.png)

- Les ampoules et tournevis apparaissent dans la marge de gauche de l’éditeur quand vous déplacez le signe insertion dans une ligne de code pour lequel une action rapide est disponible.

- Appuyez sur **Ctrl**+**.** n’importe où sur une ligne pour afficher la liste des actions rapides et refactorisations disponibles.

## <a name="to-see-potential-fixes"></a>Pour afficher les corrections éventuelles

Sélectionnez la flèche vers le bas en regard de l’ampoule ou le lien **Afficher les corrections éventuelles** pour afficher une liste des actions rapides disponibles.

![Ampoule développée](../ide/media/vs2015_lightbulb_hover_expanded.png)

## <a name="see-also"></a>Voir aussi

- [Génération de code dans Visual Studio](../ide/code-generation-in-visual-studio.md)
- [Actions rapides courantes](../ide/common-quick-actions.md)
- [Styles de code et actions rapides](../ide/code-styles-and-quick-actions.md)
- [Écrire et refactoriser du code (C++)](/cpp/ide/writing-and-refactoring-code-cpp)