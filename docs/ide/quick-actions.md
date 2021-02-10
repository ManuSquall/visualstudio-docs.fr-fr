---
title: Actions rapides, ampoules et tournevis
description: Découvrez comment utiliser une action rapide pour Refactoriser, générer ou modifier votre code.
ms.custom: SEO-VS-2020
ms.date: 03/28/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e1d9c257bcf0e2a88a384c22010abb08894483ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951093"
---
# <a name="quick-actions"></a>Actions rapides

Les actions rapides vous permettent de refactoriser, générer ou modifier facilement le code en une seule action. Les actions rapides sont disponibles pour les fichiers C#, [C++](/cpp/ide/writing-and-refactoring-code-cpp) et Visual Basic. Certaines actions sont spécifiques à un langage, d’autres s’appliquent à tous les langages.

Les actions rapides peuvent servir à :

- Appliquer un correctif de code pour une violation de règle de l' [Analyseur de code](../code-quality/roslyn-analyzers-overview.md)

::: moniker range=">=vs-2019"

- [Supprimer](../code-quality/use-roslyn-analyzers.md#suppress-violations) une violation de règle de l’analyseur de code ou [configurer](../code-quality/use-roslyn-analyzers.md#set-rule-severity-from-the-light-bulb-menu) sa gravité

::: moniker-end

::: moniker range="vs-2017"

- [Supprimer](../code-quality/use-roslyn-analyzers.md#suppress-violations) une violation de règle de l’analyseur de code

::: moniker-end

- Appliquer une refactorisation (par exemple, [inline une variable temporaire](../ide/reference/inline-temporary-variable.md))

- Générer du code (par exemple, [introduire une variable locale](../ide/reference/introduce-local-variable.md))

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Refactorisation (Visual Studio pour Mac)](/visualstudio/mac/refactoring).

Les actions rapides peuvent être appliquées à l’aide de l’icône d’ampoule de l’ampoule ou des icônes de l' ![ ](media/light-bulb-icon.png) icône du tournevis Tournevis ![ ](media/screwdriver-icon.png) , ou en appuyant sur **CTRL** + **.** lorsque le curseur se trouve sur une ligne de code pour laquelle une action est disponible. Vous voyez une ampoule d’erreur ![icône en forme d’ampoule d’erreur](media/error-light-bulb-icon.png) s’il existe une ligne ondulée rouge indiquant une erreur, pour laquelle Visual Studio met à disposition un correctif.

Des éditeurs tiers peuvent fournir des diagnostics et des suggestions personnalisés pour n’importe quel langage, par exemple dans le cadre d’un Kit de développement logiciel (SDK). Dans ce cas, les ampoules Visual Studio s’affichent en fonction des règles établies.

## <a name="icons"></a>Icônes

L’icône qui s’affiche quand une action rapide est disponible donne une indication du type de correctif ou de refactorisation disponible. L’icône en forme de *tournevis* ![icône en forme de tournevis](media/screwdriver-icon.png) indique simplement que des actions sont disponibles pour modifier le code, mais vous ne devez pas nécessairement les utiliser. L’icône en forme *d’ampoule jaune* ![icône en forme d’ampoule](media/light-bulb-icon.png) indique qu’il existe des actions disponibles que vous *devez* effectuer pour améliorer votre code. L’icône en forme *d’ampoule d’erreur* ![icône en forme d’ampoule d’erreur](media/error-light-bulb-icon.png) indique qu’une action est disponible pour résoudre une erreur dans votre code.

## <a name="to-see-a-light-bulb-or-screwdriver"></a>Pour afficher une ampoule ou un tournevis

Si un correctif est disponible, les ampoules apparaissent :

- Lorsque vous pointez la souris à l’emplacement d’une erreur

   ![Ampoule avec pointage de la souris](../ide/media/vs2015_lightbulb_hover.png)

- Dans la marge gauche de l’éditeur lorsque vous déplacez le point d’insertion (curseur) dans la ligne de code concernée

Vous pouvez également appuyer sur **CTRL** + **.** n’importe où sur une ligne pour afficher la liste des actions rapides et refactorisations disponibles.

Pour afficher les corrections éventuelles, sélectionnez la flèche vers le bas en regard de l’ampoule ou le lien **Afficher les corrections éventuelles**. Une liste des actions rapides disponibles s’affiche.

![Ampoule développée](../ide/media/vs2015_lightbulb_hover_expanded.png)

## <a name="see-also"></a>Voir aussi

- [Génération de code dans Visual Studio](../ide/code-generation-in-visual-studio.md)
- [Actions rapides courantes](../ide/common-quick-actions.md)
- [Styles de code et actions rapides](../ide/code-styles-and-code-cleanup.md)
- [Écrire et refactoriser du code (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [Refactorisation (Visual Studio pour Mac)](/visualstudio/mac/refactoring)
