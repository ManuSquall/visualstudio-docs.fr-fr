---
title: Guide pratique pour définir les options d’accessibilité IDE
description: Découvrez comment définir les options d’accessibilité dans Visual Studio qui facilitent l’utilisation de son environnement de développement intégré (IDE) pour tout le monde, y compris pour les personnes ayant des difficultés à lire ou à écrire.
ms.date: 08/23/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: how-to
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac857d961b1ae736645ba2cfda3f1ef5755d0fa1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85770279"
---
# <a name="how-to-set-ide-accessibility-options"></a>Guide pratique pour définir les options d’accessibilité IDE

Visual Studio contient des fonctionnalités qui facilitent la lecture pour les personnes à acuité visuelle réduite et l’écriture pour celles dont la dextérité manuelle est réduite. Par exemple, vous pouvez modifier la taille et la couleur du texte dans les éditeurs, modifier la taille du texte et des boutons sur les barres d’outils et modifier les paramètres pour vous aider à exécuter une fonction ou une instruction.

En outre, Visual Studio prend en charge les dispositions de clavier Dvorak, qui rendent plus accessibles les caractères les plus fréquemment tapés. Vous pouvez également personnaliser les raccourcis clavier par défaut disponibles dans Visual Studio. Pour plus d’informations, consultez [Identifier et personnaliser les raccourcis clavier](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites ici, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Paramètres d'importation et d'exportation** dans le menu **Outils** . Pour plus d’informations, consultez [Réinitialiser les paramètres](../environment-settings.md#reset-settings).

::: moniker range="vs-2017"

> [!TIP]
> Pour en savoir plus sur les dernières nouveautés en matière d’accessibilité, consultez le billet de blog [Améliorations apportées à l’accessibilité dans Visual Studio 2017 version 15.3](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/).

::: moniker-end

## <a name="editors-dialogs-and-tool-windows"></a>Éditeurs, boîtes de dialogue et fenêtres d’outils

Par défaut, les boîtes de dialogue et les fenêtres d’outils de Visual Studio utilisent les mêmes taille de police et couleurs que le système d’exploitation. Les paramètres de couleur pour le cadre de l’IDE, les boîtes de dialogue, les barres d’outils et les fenêtres d’outils sont basés sur un modèle de couleurs : clair ou sombre. Vous pouvez modifier le thème de couleur actuel dans la [boîte de dialogue Options : environnement > général](../../ide/reference/general-environment-options-dialog-box.md).

Vous pouvez également afficher des fenêtres indépendantes dans le mode Code de l’éditeur. Ces fenêtres peuvent vous demander de fournir des membres disponibles sur l’objet en cours et les paramètres pour exécuter une fonction ou une instruction. Ces fenêtres peuvent être utiles si vous avez des difficultés à taper. Toutefois, elles interfèrent avec le focus dans l’éditeur de code, ce qui peut être problématique pour certains utilisateurs.

Voici comment désactiver les fenêtres indépendantes :

1. Dans le menu **Outils** , choisissez **Options**.

1. Choisissez **éditeur de texte**  >  **tous les langages**  >  **général**.

1. Désactivez les cases à cocher **Répertorier automatiquement les membres** et **Informations sur les paramètres**.

Vous pouvez réorganiser les fenêtres dans l’environnement de développement intégré (IDE) pour les adapter au mieux à votre manière de travailler. Vous pouvez ancrer, rendre flottante, masquer ou masquer automatiquement chaque fenêtre Outil. Pour plus d’informations sur la modification des dispositions de fenêtres, consultez [Personnaliser les dispositions de fenêtres](../../ide/customizing-window-layouts-in-visual-studio.md).

### <a name="change-the-size-of-text"></a>Changer la taille du texte

Vous pouvez modifier les paramètres des fenêtres Outil de texte, telles que la fenêtre **Commande**, la fenêtre **Exécution** et la fenêtre **Sortie** en utilisant **Outils** > **Options** > **Environnement** > **Polices et couleurs**.

Lorsque l’option **[Toutes les fenêtres Outil de texte]** est sélectionnée dans la liste déroulante **Afficher les paramètres de**, le paramètre par défaut est répertorié en tant que **Par défaut** dans les listes déroulantes **Premier plan de l’élément** et **Arrière plan de l’élément**. Choisissez le bouton **Personnalisé** pour modifier ces paramètres.

Vous pouvez également modifier les paramètres d’affichage du texte dans l’éditeur. Voici comment faire.

1. Dans le menu **Outils** , choisissez **Options**.

1. Choisissez **Environment**  >  **les polices et les couleurs de**l’environnement.

1. Sélectionnez une option dans le menu déroulant **Afficher les paramètres de**.

    Pour modifier la taille de police du texte dans un éditeur, choisissez **Éditeur de texte**.

    Pour modifier la taille de police du texte dans les fenêtres Outil de texte, choisissez **[Toutes les fenêtres Outil de texte]**.

    Pour modifier la taille de police du texte des info-bulles dans un éditeur, choisissez **Info-bulle de l’éditeur**.

    Pour modifier la taille de police du texte dans la saisie semi-automatique des instructions, choisissez **Saisie semi-automatique des instructions**.

1. Dans **Afficher les éléments**, sélectionnez **Texte brut**.

1. Dans **Police**, sélectionnez un nouveau type de police.

1. Dans **Taille**, sélectionnez une nouvelle taille de police.

    > [!TIP]
    > Pour rétablir la taille du texte pour les éditeurs et les fenêtres Outil de texte, choisissez **Par défaut**.

7. Choisissez **OK**.

### <a name="change-the-colors-that-are-used-in-the-ide"></a>Changer les couleurs utilisées dans l’IDE

Vous pouvez choisir de modifier les couleurs par défaut pour le texte, les indicateurs en marge, l’espace blanc et les éléments de code dans l’éditeur. Voici comment faire.

1. Dans le menu **Outils** , choisissez **Options**.

1. Dans le dossier **Environnement**, choisissez **Polices et couleurs**.

1. Dans **Afficher les paramètres de**, choisissez **Éditeur de texte**.

1. Dans **Afficher les éléments**, sélectionnez un élément dont vous avez besoin de modifier l’affichage, tel que **Texte brut**, **Marge des indicateurs**, **Espaces blancs visibles**, **Nom d’attribut HTML** ou **Attribut XML**.

1. Sélectionnez les paramètres d’affichage parmi les options suivantes : **Premier plan de l’élément**, **Arrière-plan de l’élément** et **Gras**.

1. Choisissez **OK**.

> [!TIP]
> Pour utiliser des couleurs à contraste élevé pour toutes les fenêtres d’application sur votre système d’exploitation, appuyez sur **ALT**gauche + **MAJ gauche** + **Impr**. écran. Si Visual Studio est ouvert, fermez-le et rouvrez-le pour implémenter complètement les couleurs à contraste élevé.

## <a name="toolbars"></a>Barres d'outils

Pour améliorer l’accessibilité et la facilité d’utilisation de la barre d’outils, vous pouvez ajouter du texte aux boutons de barre d’outils.

### <a name="to-assign-text-to-toolbar-buttons"></a>Pour affecter un texte à des boutons de barre d’outils

1. Dans le menu **Outils**, choisissez **Personnaliser**.

1. Dans la boîte de dialogue **Personnaliser**, sélectionnez l’onglet **Commandes**.

1. Sélectionnez **Barre d’outils**, puis choisissez le nom de la barre d’outils qui contient le bouton pour lequel vous souhaitez afficher le texte.

1. Dans la liste, sélectionnez la commande que vous souhaitez modifier.

1. Choisissez **Modifier la sélection**.

1. Choisissez **Image et texte**.

### <a name="to-modify-the-displayed-text-in-a-button"></a>Pour modifier le texte à afficher dans un bouton

1. Sélectionnez de nouveau **Modifier la sélection**.

1. À côté de **Nom**, insérez une nouvelle légende pour le bouton sélectionné.

## <a name="see-also"></a>Voir aussi

* [Fonctionnalités d’accessibilité de Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Accessibilité de Visual Studio pour Mac](/visualstudio/mac/accessibility/)
* [Ressources pour la conception d’applications accessibles](../../ide/reference/resources-for-designing-accessible-applications.md)
