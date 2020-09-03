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
ms.openlocfilehash: 07ad01726b57073cad3a5a2876a4b22667d3770a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545442"
---
# <a name="outlining"></a>mode Plan

Vous pouvez choisir de masquer du code dans la vue en réduisant une région de code pour qu’elle apparaisse sous un signe plus ( **+** ). Pour développer une zone réduite, vous devez cliquer sur le signe plus (+). Si vous êtes un utilisateur du clavier, vous pouvez choisir **CTRL** + **m** + **m** pour réduire et développer. Vous pouvez aussi réduire une zone en mode Plan en double-cliquant sur n’importe quelle ligne dans la zone dans la marge de mode Plan, affichée juste à gauche du code. Vous pouvez afficher le contenu d’une zone réduite sous forme d’info-bulle quand vous pointez sur la partie réduite.

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Éditeur de code Source (Visual Studio pour Mac)](/visualstudio/mac/source-editor).

Les zone dans la marge de mode Plan sont également mises en surbrillance quand vous pointez sur la marge avec la souris. La couleur de mise en surbrillance par défaut peut sembler plutôt fade dans certaines configurations de couleur. Vous pouvez le modifier dans **Outils**  >  **options**  >  **environnement**  >  **polices et couleurs**  >  **zone réductible**.

Quand vous travaillez dans du code en mode Plan, vous pouvez développer les sections sur lesquelles vous souhaitez travailler, les réduire quand vous avez terminé, puis basculer vers d’autres sections. Quand vous ne souhaitez pas afficher le mode Plan, vous pouvez utiliser la commande **Arrêter le mode Plan** pour supprimer les informations de mode Plan sans endommager le code sous-jacent.

Les commandes **Annuler** et **Restaurer** du menu **Edition** affectent ces actions. Les opérations **Copier**, **Couper**, **Coller** et glisser-déplacer conservent les informations de mode Plan, mais pas l’état de la zone réductible. Par exemple, quand vous copiez une zone réduite, l’opération **Coller** colle le texte copié en tant que zone développée.

> [!CAUTION]
> Quand vous modifiez une zone en mode Plan, vous risquez de perdre le mode Plan. Par exemple, une suppression ou une opération de remplacement peut effacer la fin de la zone.

Les commandes suivantes se trouvent dans le sous **Edit**  >  -menu modifier le**mode plan** .

|Nom|Description|
|-|-|
|Masquer la sélection|(**CTRL** + **M**, **CTRL** + **H**)-réduit un bloc de code sélectionné qui ne serait normalement pas disponible pour le mode plan, par exemple un `if` bloc. Pour supprimer la zone personnalisée, utilisez **Arrêter le masquage actuel** (ou **Ctrl**+**M**, **Ctrl**+**U**). Non disponible en Visual Basic.|
|Activer/Désactiver le développement du mode Plan|- Inverse l’état masqué ou développé actuel de la section en mode Plan la plus intérieure quand le curseur se trouve dans une section réduite imbriquée.|
|Activer/Désactiver toutes les régions en mode Plan|(**CTRL** + **M**, **CTRL** + **L**)-définit toutes les régions sur le même État réduit ou développé. Si certaines zones sont développées et d’autres réduites, les zones réduites sont développées.|
|Arrêter le mode Plan|(**CTRL** + **M**, **CTRL** + **P**)-supprime toutes les informations en mode plan pour le document entier.|
|Arrêter le masquage actuel|(**CTRL** + **M**, **CTRL** + **U**)-supprime les informations de mode plan pour la zone définie par l’utilisateur actuellement sélectionnée. Non disponible en Visual Basic.|
|Réduire aux définitions|(**CTRL** + **M**, **CTRL** + **O**)-réduit les membres de tous les types.|
|Réduire le bloc :\<logical boundary>|C++ Réduit une zone dans la fonction contenant le point d’insertion. Par exemple, si le point d’insertion se trouve à l’intérieur d’une boucle, celle-ci est masquée.|
|Réduire tout dans : \<logical structures>|C++ Réduit toutes les structures à l’intérieur de la fonction.|

Vous pouvez également utiliser le SDK Visual Studio pour définir les zones de texte que vous souhaitez développer ou réduire. Consultez [Procédure pas à pas : mode Plan](../extensibility/walkthrough-outlining.md).

## <a name="see-also"></a>Voir aussi

- [Fonctionnalités de l’éditeur de code](../ide/writing-code-in-the-code-and-text-editor.md)
- [Éditeur de code source (Visual Studio pour Mac)](/visualstudio/mac/source-editor)
