---
title: Modifier les thèmes, les polices, le texte et le contraste pour l’accessibilité
description: Découvrez comment modifier les thèmes de couleurs, les couleurs de police, les tailles de texte et les couleurs de contraste supplémentaires de Visual Studio pour des raisons de simplicité d’utilisation et d’accessibilité.
ms.date: 08/20/2020
ms.topic: how-to
ms.custom: contperfq1
helpviewer_keywords:
- Visual Studio, color themes
- color themes, Visual Studio
ms.assetid: 60d91ba1-244b-4c43-847f-60b744f1352a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b2410974ed95b1aa8dca3dc3e31a39c39df2d4a0
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88801436"
---
# <a name="how-to-change-fonts-colors-and-themes-in-visual-studio"></a>Comment : modifier les polices, les couleurs et les thèmes dans Visual Studio

Vous pouvez modifier les polices et les couleurs dans Visual Studio de plusieurs façons. Par exemple, vous pouvez remplacer le thème de couleur bleu par défaut par le thème sombre (également appelé « mode sombre »). Vous pouvez également sélectionner un thème à contraste élevé si cela répond le mieux à vos besoins. Et vous pouvez modifier la police et la taille du texte par défaut dans l’IDE et l’éditeur de code.

## <a name="change-the-color-theme"></a>Changer le thème de couleur

Voici comment modifier le thème de couleur du frame IDE et les fenêtres outil dans Visual Studio.

1. Dans la barre de menus, choisissez **Outils**  >  **options**.

1. Dans la liste options, choisissez **environnement**  >  **général**.

1. Dans la **liste thème de couleur** , choisissez le thème **bleu** par défaut, le thème **clair** , le thème **foncé** ou le thème **bleu (contraste supplémentaire)** .

   ![Capture d’écran de la boîte de dialogue Options pour modifier le thème de couleur](media/fonts-colors-theme.png "Capture d’écran de la boîte de dialogue Options que vous pouvez utiliser pour modifier le thème de couleur")

    > [!NOTE]
    > Lorsque vous modifiez un thème de couleur, le texte dans l’IDE revient à la valeur par défaut ou aux polices et tailles précédemment personnalisées pour ce thème.

    :::moniker range="vs-2017"

    > [!TIP]
    > Vous pouvez créer et modifier vos propres thèmes Visual Studio en installant l' [éditeur de thème de couleurs pour Visual studio 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor).

    :::moniker-end

    :::moniker range="vs-2019"

    > [!TIP]
    > Vous pouvez créer et modifier vos propres thèmes Visual Studio en installant le [Concepteur de thèmes de couleurs de Visual Studio](https://marketplace.visualstudio.com/items?itemName=ms-madsk.ColorThemeDesigner).

    :::moniker-end

## <a name="change-fonts-and-text-size"></a>Modifier les polices et la taille du texte

Vous pouvez modifier la police et la taille du texte pour toutes les fenêtres Frame et outil IDE, ou uniquement pour certains éléments Windows ou Text. Vous pouvez également modifier la police et la taille du texte dans l’éditeur.

### <a name="to-change-the-font-and-text-size-in-the-ide"></a>Pour modifier la police et la taille du texte dans l’IDE

1. Dans la barre de menus, choisissez **Outils**  >  **options**.

1. Dans la liste options, choisissez **Environment**  >  **polices et couleurs**de l’environnement.

1. Dans la liste **afficher les paramètres de** , choisissez **environnement**.

   ![Capture d’écran de la boîte de dialogue Options pour modifier les polices et les couleurs dans l’IDE](media/fonts-colors-environment.png "Capture d’écran de la boîte de dialogue Options pour modifier les polices et les couleurs dans l’IDE")

    > [!NOTE]
    > Pour changer la police des fenêtres Outil uniquement, dans la liste **Afficher les paramètres de**, choisissez **Toutes les fenêtres Outil de texte**.

1. Modifiez les options de **police** et de **taille** pour modifier la police et la taille du texte de l’IDE.

1. Sélectionnez l’élément approprié dans **Éléments affichés**, puis modifiez les options **Premier plan de l’élément** et **Arrière-plan de l’élément**.

### <a name="to-change-the-font-and-text-size-in-the-editor"></a>Pour modifier la police et la taille du texte dans l’éditeur

1. Dans la barre de menus, choisissez **Outils**  >  **options**.

1. Dans la liste options, choisissez **Environment**  >  **polices et couleurs**de l’environnement.

1. Dans **afficher les paramètres de** la liste, sélectionnez **éditeur de texte**.

   ![Capture d’écran de la boîte de dialogue Options pour modifier les polices et les couleurs dans l’éditeur](media/fonts-colors-text-editor.png "Capture d’écran de la boîte de dialogue Options pour modifier les polices et les couleurs de l’éditeur")

1. Modifiez les options de **police** et de **taille** pour modifier la police et la taille du texte de l’éditeur.

1. Sélectionnez l’élément approprié dans **Éléments affichés**, puis modifiez les options **Premier plan de l’élément** et **Arrière-plan de l’élément**.

Pour plus d’informations, consultez la page [modifier les polices et les couleurs de l’éditeur](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md) .

## <a name="accessibility-options"></a>Options d’accessibilité

Il existe des options de thème de couleurs pour vous si vous rencontrez une acuité visuelle faible. Vous pouvez utiliser une option de contraste élevé pour *toutes* les applications et l’interface utilisateur sur un ordinateur, ou une option de contraste supplémentaire pour Visual Studio uniquement.

### <a name="use-windows-high-contrast"></a>Utiliser le contraste élevé Windows

Utilisez l’une des procédures suivantes pour activer ou désactiver l’option contraste élevé de Windows :

- Dans Windows ou dans n’importe quelle application Microsoft, appuyez sur la touche **ALT**gauche + **MAJ gauche**de l’écran + **PrtScn** .

- Dans Windows, choisissez **Start**  >  **paramètres**  >  **de démarrage facilité d’accès**  >  **contraste élevé**.

    > [!WARNING]
    > Le paramètre contraste élevé de Windows affecte toutes les applications et l’interface utilisateur sur l’ordinateur.

### <a name="use-visual-studio-extra-contrast"></a>Utiliser le contraste supplémentaire de Visual Studio

Utilisez les procédures suivantes pour activer ou désactiver l’option contraste supplémentaire de Visual Studio :

1. Dans la barre de menus de Visual Studio, choisissez **Outils**  >  **options**, puis, dans la liste options, choisissez **environnement**  >  **général**.

1. Dans la liste déroulante **thème de couleur** , choisissez le thème **bleu (contraste supplémentaire)** , puis choisissez **OK**.

Pour en savoir plus sur les autres options d’accessibilité de Visual Studio à votre disposition, consultez la page [fonctionnalités d’accessibilité de Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md) .

> [!TIP]
> S’il existe une option d’accessibilité pour les couleurs ou les polices qui peuvent être utiles, mais n’est pas disponible actuellement dans Visual Studio, faites-le nous savoir en sélectionnant **suggérer une fonctionnalité** dans la [communauté des développeurs Visual Studio](https://developercommunity.visualstudio.com/). Pour plus d’informations sur ce forum et son fonctionnement, consultez la page [suggérer une fonctionnalité](../ide/suggest-a-feature.md) .

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur tous les éléments d’interface utilisateur pour lesquels vous pouvez modifier les jeux de polices et de couleurs, consultez la page de boîte de [dialogue polices et couleurs, environnement, options](../ide/reference/fonts-and-colors-environment-options-dialog-box.md) .

## <a name="see-also"></a>Voir aussi

- [Comment : modifier les polices et les couleurs de l’éditeur dans Visual Studio](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md)
- [Fonctionnalités de l’éditeur de code Visual Studio](../ide/writing-code-in-the-code-and-text-editor.md)
- [Personnaliser l’IDE de Visual Studio et l’éditeur](../ide/quickstart-personalize-the-ide.md)