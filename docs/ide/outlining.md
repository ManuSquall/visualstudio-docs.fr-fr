---
title: Réduire et développer des régions de code
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- Visual Studio, expand/collapse code
- Visual Studio, outlining
- expand/collapse code
- code [Visual Studio], outlining
- code [Visual Studio], hiding
- outlining code
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 781c9a6bc30f7d3a29bcb89e743600e6b29e6445
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585754"
---
# <a name="outlining"></a>Mode Plan

Vous pouvez choisir de cacher un code de la vue en s’effondrant une région de code de sorte qu’il apparaît sous un signe positif (**+**). Pour développer une zone réduite, vous devez cliquer sur le signe plus (+). Si vous êtes un utilisateur de clavier, vous pouvez choisir **Ctrl**+**M**+**M** pour s’effondrer et se développer. Vous pouvez aussi réduire une zone en mode Plan en double-cliquant sur n’importe quelle ligne dans la zone dans la marge de mode Plan, affichée juste à gauche du code. Vous pouvez afficher le contenu d’une zone réduite sous forme d’info-bulle quand vous pointez sur la partie réduite.

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Éditeur de code Source (Visual Studio pour Mac)](/visualstudio/mac/source-editor).

Les zone dans la marge de mode Plan sont également mises en surbrillance quand vous pointez sur la marge avec la souris. La couleur de mise en surbrillance par défaut peut sembler plutôt fade dans certaines configurations de couleur. Vous pouvez le modifier dans **Tools** > **Options** > **Environment** > **Fonts et Colors** > **Collapsible Region**.

Quand vous travaillez dans du code en mode Plan, vous pouvez développer les sections sur lesquelles vous souhaitez travailler, les réduire quand vous avez terminé, puis basculer vers d’autres sections. Quand vous ne souhaitez pas afficher le mode Plan, vous pouvez utiliser la commande **Arrêter le mode Plan** pour supprimer les informations de mode Plan sans endommager le code sous-jacent.

Les commandes **Annuler** et **Restaurer** du menu **Edition** affectent ces actions. Les opérations **Copier**, **Couper**, **Coller** et glisser-déplacer conservent les informations de mode Plan, mais pas l’état de la zone réductible. Par exemple, quand vous copiez une zone réduite, l’opération **Coller** colle le texte copié en tant que zone développée.

> [!CAUTION]
> Quand vous modifiez une zone en mode Plan, vous risquez de perdre le mode Plan. Par exemple, une suppression ou une opération de remplacement peut effacer la fin de la zone.

Les commandes suivantes peuvent être trouvées sur le sous-mois **Edit** > **Outlining.**

|||
|-|-|
|Masquer la sélection|(**Ctrl**+**M**, **Ctrl**+**H**) - Effondre un bloc de code sélectionné qui `if` ne serait normalement pas disponible pour la mise en ligne, par exemple un bloc. Pour supprimer la zone personnalisée, utilisez **Arrêter le masquage actuel** (ou **Ctrl**+**M**, **Ctrl**+**U**). Non disponible en Visual Basic.|
|Activer/Désactiver le développement du mode Plan|- Inverse l’état masqué ou développé actuel de la section en mode Plan la plus intérieure quand le curseur se trouve dans une section réduite imbriquée.|
|Activer/Désactiver toutes les régions en mode Plan|(**Ctrl**+**M**, **Ctrl**+**L**) - Définit toutes les régions à la même état effondré ou élargi. Si certaines zones sont développées et d’autres réduites, les zones réduites sont développées.|
|Arrêter le mode Plan|(**Ctrl**+**M**, **Ctrl**+**P**) - Supprime toutes les informations décrivant pour l’ensemble du document.|
|Arrêter le masquage actuel|(**Ctrl**+**M**, **Ctrl**+**U**) - Supprime les informations décrivantes pour la région actuellement sélectionnée définie par l’utilisateur. Non disponible en Visual Basic.|
|Réduire aux définitions|(**Ctrl**+**M**, **Ctrl**+**O**) - Effondre les membres de tous types.|
|Réduire le bloc :\<limite logique>|(C) Effondre une région dans la fonction contenant le point d’insertion. Par exemple, si le point d’insertion se trouve à l’intérieur d’une boucle, celle-ci est masquée.|
|Réduire tout dans : \<structures logiques>|(C) Effondre toutes les structures à l’intérieur de la fonction.|

Vous pouvez également utiliser le SDK Visual Studio pour définir les zones de texte que vous souhaitez développer ou réduire. Consultez [Procédure pas à pas : mode Plan](../extensibility/walkthrough-outlining.md).

## <a name="see-also"></a>Voir aussi

- [Fonctionnalités de l’éditeur de code](../ide/writing-code-in-the-code-and-text-editor.md)
- [Éditeur de code source (Visual Studio pour Mac)](/visualstudio/mac/source-editor)
