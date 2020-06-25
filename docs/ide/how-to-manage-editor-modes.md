---
title: Mode Plein écran et mode Espace virtuel
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- word wrap
- views, virtual space
- line numbers, displaying
- virtual space mode
- line numbers
- Code Editor, view and display options
- full screen mode
- Code Editor, modes
- views, splitting
- views, word wrapping
- fonts and size
- views, creating new windows
- views, line numbers
- views, changing mode
- views, outlining
ms.assetid: 1fb48027-d870-439f-8b72-4a0321390748
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f8f86d635e1e57d82dd2d18084c91a9267f9a0b
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284202"
---
# <a name="how-to-manage-editor-modes"></a>Guide pratique pour gérer les modes de l’éditeur

Vous pouvez afficher l’éditeur de code Visual Studio dans différents modes d’affichage.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s’affichent peuvent être différentes de celles qui sont décrites dans cet article, en fonction de vos paramètres actifs ou de l’édition utilisée. Pour modifier vos paramètres, par exemple pour définir les paramètres **Général** ou **Visual C++**, choisissez **Outils** > **Importation et exportation de paramètres**, puis choisissez **Réinitialiser tous les paramètres**.

## <a name="enable-full-screen-mode"></a>Activer le mode Plein écran

Vous pouvez choisir de masquer toutes les fenêtres outil et d’afficher uniquement les fenêtres de document en activant le mode **plein écran** .

- Appuyez sur **ALT** + **MAJ** + **entrée** pour entrer ou quitter le mode **plein écran** .

     - ou -

- Exécutez la commande `View.Fullscreen` dans la fenêtre **Commande**.

## <a name="enable-virtual-space-mode"></a>Activer le mode Espace virtuel

En mode **Espace virtuel**, des espaces sont insérés à la fin de chaque ligne de code. Sélectionnez cette option pour placer des commentaires en un point précis, proche de votre code.

1. Sélectionnez **Options** dans le menu **Outils**.

2. Développez le dossier **Éditeur de texte** et choisissez **Tous les langages** pour définir cette option globalement, ou choisissez un dossier de langage spécifique. Par exemple, pour activer les numéros de ligne uniquement dans Visual Basic, choisissez **Basic**le  >  nœud Éditeur de**texte** de base.

3. Sélectionnez les options **Général**, puis, sous **Paramètres**, sélectionnez **Activer l’espace virtuel**.

    > [!NOTE]
    > **Espace virtuel** est activé dans le mode **Sélectionner les colonnes**. Lorsque le mode **Espace virtuel** n’est pas activé, le point d’insertion passe de la fin d’une ligne directement au premier caractère de la suivante.

## <a name="see-also"></a>Voir aussi

- [Personnalisation des dispositions de fenêtres dans Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md)
- [Polices et couleurs, environnement, boîte de dialogue Options](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)
