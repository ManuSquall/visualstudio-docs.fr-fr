---
title: Actions rapides | Microsoft Docs
ms.date: 03/28/2018
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
ms.openlocfilehash: 941980eff8fc2474df9555b326278abdb9b26dac
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="quick-actions"></a>Actions rapides

Les actions rapides vous permettent de refactoriser, générer ou modifier facilement le code en une seule action. Les actions rapides sont disponibles pour les fichiers C#, [C++](/cpp/ide/writing-and-refactoring-code-cpp) et Visual Basic. Certaines actions sont spécifiques à un langage, d’autres s’appliquent à tous les langages.

Les actions rapides peuvent servir à :

- appliquer un correctif de code en cas de violation de règle de [l’analyseur de code](../code-quality/roslyn-analyzers-overview.md) ;
- [supprimer](../code-quality/use-roslyn-analyzers.md) une violation de règle de l’analyseur de code ;
- appliquer une refactorisation (par exemple, [rendre inline une variable temporaire](../ide/reference/inline-temporary-variable.md)) ;
- générer du code (par exemple, [introduire une variable locale](../ide/reference/introduce-local-variable.md)).

Les actions rapides peuvent être appliquées en utilisant l’icône d’ampoule ![Petite icône en forme d’ampoule](media/vs2015_lightbulbsmall.png) ou en appuyant sur **Ctrl**+**.** lorsque le curseur se trouve sur une ligne de code pour laquelle une action est disponible. Une ampoule apparaît si votre code est souligné d’une ligne ondulée rouge et qu’une suggestion pour résoudre le problème est disponible dans Visual Studio. Par exemple, si une erreur est signalée par un soulignement rouge ondulé, une ampoule apparaît lorsque des corrections sont disponibles pour cette erreur.

Des éditeurs tiers peuvent fournir des diagnostics et des suggestions personnalisés pour n’importe quel langage, par exemple dans le cadre d’un Kit de développement logiciel (SDK). Dans ce cas, les ampoules Visual Studio s’allument en fonction des règles établies.

## <a name="to-see-a-light-bulb"></a>Pour afficher une ampoule

1. Dans de nombreux cas, les ampoules apparaissent spontanément au passage de la souris au niveau de l’erreur ou dans la marge gauche de l’éditeur lorsque le point d’insertion est déplacé dans une ligne comportant une erreur. Si vous remarquez une ligne ondulée rouge, vous pouvez pointer dessus avec la souris pour afficher l'ampoule. Vous pouvez aussi déclencher l'apparition d'une ampoule quand vous utilisez la souris ou le clavier pour vous rendre quelque part sur la ligne où le problème se produit.

1. Appuyez sur **Ctrl**+**.** sur une ligne pour appeler l’ampoule et accéder directement à la liste des corrections éventuelles.

   ![Ampoule avec pointage de la souris](../ide/media/vs2015_lightbulb_hover.png)

## <a name="to-see-potential-fixes"></a>Pour afficher les corrections éventuelles

Cliquez sur la flèche bas ou sur le lien Afficher les corrections éventuelles pour afficher une liste d'actions rapides que l'ampoule peut effectuer pour vous.

![Ampoule développée](../ide/media/vs2015_lightbulb_hover_expanded.png)

## <a name="see-also"></a>Voir aussi

- [Génération de code dans Visual Studio](../ide/code-generation-in-visual-studio.md)
- [Actions rapides courantes](../ide/common-quick-actions.md)
- [Styles de code et actions rapides](../ide/code-styles-and-quick-actions.md)
- [Écriture et refactorisation du code (C++)](/cpp/ide/writing-and-refactoring-code-cpp)