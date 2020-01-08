---
title: Actions rapides, ampoules et tournevis
ms.date: 03/28/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2ce8ce85e027a7ed7f78d0da1f68f328c1ca103d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596955"
---
# <a name="quick-actions"></a>Actions rapides

Les actions rapides vous permettent de refactoriser, générer ou modifier facilement le code en une seule action. Les actions rapides sont disponibles pour les fichiers C#, [C++](/cpp/ide/writing-and-refactoring-code-cpp) et Visual Basic. Certaines actions sont spécifiques à un langage, d’autres s’appliquent à tous les langages.

Les actions rapides peuvent servir à :

- appliquer un correctif de code en cas de violation de règle de [l’analyseur de code](../code-quality/roslyn-analyzers-overview.md) ;

::: moniker range=">=vs-2019"

- [Supprimer](../code-quality/use-roslyn-analyzers.md#suppress-violations) une violation de règle de l’analyseur de code ou [configurer](../code-quality/use-roslyn-analyzers.md#automatically-configure-rule-severity) sa gravité

::: moniker-end

::: moniker range="vs-2017"

- [supprimer](../code-quality/use-roslyn-analyzers.md#suppress-violations) une violation de règle de l’analyseur de code ;

::: moniker-end

- appliquer une refactorisation (par exemple, [rendre inline une variable temporaire](../ide/reference/inline-temporary-variable.md)) ;

- générer du code (par exemple, [introduire une variable locale](../ide/reference/introduce-local-variable.md)).

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Refactorisation (Visual Studio pour Mac)](/visualstudio/mac/refactoring).

Les actions rapides peuvent être appliquées en utilisant l’icône en forme d’ampoule ![icône en forme d’ampoule](media/light-bulb-icon.png) ou de tournevis ![icône en forme de tournevis](media/screwdriver-icon.png), ou en appuyant sur **Ctrl**+ **.** lorsque le curseur se trouve sur une ligne de code pour laquelle une action est disponible. Vous voyez une ampoule d’erreur ![icône en forme d’ampoule d’erreur](media/error-light-bulb-icon.png) s’il existe une ligne ondulée rouge indiquant une erreur, pour laquelle Visual Studio met à disposition un correctif.

Des éditeurs tiers peuvent fournir des diagnostics et des suggestions personnalisés pour n’importe quel langage, par exemple dans le cadre d’un Kit de développement logiciel (SDK). Dans ce cas, les ampoules Visual Studio s’affichent en fonction des règles établies.

## <a name="icons"></a>Icônes

L’icône qui s’affiche quand une action rapide est disponible donne une indication du type de correctif ou de refactorisation disponible. Le *tournevis* ![icône de tournevis](media/screwdriver-icon.png) icône indique simplement qu’il y a des actions disponibles pour modifier le code, mais vous ne devez pas nécessairement les utiliser. L’icône d’ampoule *jaune* ![icône d’ampoule](media/light-bulb-icon.png) *indique que des* actions sont disponibles pour améliorer votre code. L' *icône d’ampoule d'* erreur ![icône d’ampoule](media/error-light-bulb-icon.png) icône indique qu’une action est disponible pour corriger une erreur dans votre code.

## <a name="to-see-a-light-bulb-or-screwdriver"></a>Pour afficher une ampoule ou un tournevis

Si un correctif est disponible, les ampoules apparaissent :

- Lorsque vous pointez la souris à l’emplacement d’une erreur

   ![Ampoule avec pointage de la souris](../ide/media/vs2015_lightbulb_hover.png)

- Dans la marge gauche de l’éditeur lorsque vous déplacez le point d’insertion (curseur) dans la ligne de code concernée

Vous pouvez également appuyer sur **Ctrl**+ **.** n’importe où sur une ligne pour afficher la liste des actions rapides et refactorisations disponibles.

Pour afficher les corrections éventuelles, sélectionnez la flèche vers le bas en regard de l’ampoule ou le lien **Afficher les corrections éventuelles**. Une liste des actions rapides disponibles s’affiche.

![Ampoule développée](../ide/media/vs2015_lightbulb_hover_expanded.png)

## <a name="see-also"></a>Voir aussi

- [Génération de code dans Visual Studio](../ide/code-generation-in-visual-studio.md)
- [Actions rapides courantes](../ide/common-quick-actions.md)
- [Styles de code et actions rapides](../ide/code-styles-and-code-cleanup.md)
- [Écrire et refactoriser du code (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [Refactorisation (Visual Studio pour Mac)](/visualstudio/mac/refactoring)
