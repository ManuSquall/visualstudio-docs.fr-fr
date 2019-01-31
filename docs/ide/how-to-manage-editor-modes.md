---
title: Mode Plein écran et mode Espace virtuel
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e288c202bbba093738592c5060ee0d3a4f605c88
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54943888"
---
# <a name="how-to-manage-editor-modes"></a>Procédure : Gérer les modes de l’éditeur

Vous pouvez afficher l’éditeur de code Visual Studio dans différents modes d’affichage.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s’affichent peuvent être différentes de celles qui sont décrites dans cet article, en fonction de vos paramètres actifs ou de l’édition utilisée. Pour modifier vos paramètres, par exemple pour définir les paramètres **Général** ou **Visual C++**, choisissez **Outils** > **Importation et exportation de paramètres**, puis choisissez **Réinitialiser tous les paramètres**.

## <a name="enable-full-screen-mode"></a>Activer le mode Plein écran

Vous pouvez choisir de masquer toutes les fenêtres Outil et d’afficher uniquement les fenêtres de document en activant le mode **Plein écran**.

-   Appuyez sur **Alt**+**Maj**+**Entrée** pour activer ou désactiver le mode **Plein écran**.

     – ou –

-   Exécutez la commande `View.Fullscreen` dans la fenêtre **Commande**.

## <a name="enable-virtual-space-mode"></a>Activer le mode Espace virtuel

En mode **Espace virtuel**, des espaces sont insérés à la fin de chaque ligne de code. Sélectionnez cette option pour placer des commentaires en un point précis, proche de votre code.

1.  Sélectionnez **Options** dans le menu **Outils**.

2.  Développez le dossier **Éditeur de texte** et choisissez **Tous les langages** pour définir cette option globalement, ou choisissez un dossier de langage spécifique. Par exemple, pour activer les numéros de ligne uniquement dans Visual Basic, choisissez le nœud **Basic** > **Éditeur de texte**.

3.  Sélectionnez les options **Général**, puis, sous **Paramètres**, sélectionnez **Activer l’espace virtuel**.

    > [!NOTE]
    > **Espace virtuel** est activé dans le mode **Sélectionner les colonnes**. Lorsque le mode **Espace virtuel** n’est pas activé, le point d’insertion passe de la fin d’une ligne directement au premier caractère de la suivante.

## <a name="see-also"></a>Voir aussi

- [Personnaliser l’éditeur](../ide/customizing-the-editor.md)
- [Personnalisation des dispositions de fenêtres dans Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md)
- [Polices et couleurs, Environnement, boîte de dialogue Options](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)