---
title: Conseils et astuces d’accessibilité pour Visual Studio
description: Découvrez les conseils et astuces qui peuvent faciliter l’utilisation de l’environnement de développement intégré (IDE) Visual Studio pour tout le monde, y compris les personnes présentant un handicap.
ms.date: 08/06/2019
ms.topic: conceptual
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: 6b491d88-f79e-4686-8841-857624bdcfda
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5828fb114a4df559c46dd6ae7f64887ab48e7429
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919522"
---
# <a name="accessibility-tips-and-tricks-for-visual-studio"></a>Conseils et astuces d’accessibilité pour Visual Studio

Visual Studio inclut des fonctionnalités d’accessibilité intégrées qui sont compatibles avec les lecteurs d’écran et d’autres appareils de technologie d’assistance. Que vous souhaitiez utiliser des raccourcis clavier pour naviguer dans l’IDE, ou utiliser des thèmes à contraste élevé pour améliorer la visibilité, vous trouverez plusieurs conseils et astuces sur cette page pour savoir comment procéder.

Nous expliquons également comment utiliser des annotations pour révéler des informations utiles sur votre code, et comment définir des repères sonores pour les événements relatifs aux builds et aux points d’arrêt.

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Accessibilité pour Visual Studio pour Mac](/visualstudio/mac/accessibility).

## <a name="save-your-ide-settings"></a>Enregistrer vos paramètres IDE

Vous pouvez personnaliser votre expérience IDE en enregistrant la disposition de vos fenêtres, le schéma de configuration du clavier et d’autres préférences. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="modify-your-ide-for-high-contrast-viewing"></a>Modifier votre IDE pour un affichage à contraste élevé

Pour certaines personnes, quelques couleurs sont plus difficiles à voir. Si vous souhaitez plus de contraste quand vous codez mais que vous ne souhaitez pas utiliser les thèmes « Contraste élevé » classiques, nous proposons désormais un thème « Bleu (contraste supplémentaire) ».

  ![Comparer le thème Bleu et le thème Bleu (contraste supplémentaire)](media/blue-extra-contrast-theme.png "Capture d’écran montrant une comparaison entre le thème Bleu et le thème Bleu (contraste supplémentaire)")

## <a name="use-annotations-to-reveal-useful-information-about-your-code"></a>Utiliser des annotations pour révéler des informations utiles sur votre code

L’éditeur Visual Studio inclut de nombreux « ornements » de texte, qui vous donnent des informations sur des caractéristiques et des fonctionnalités à des endroits spécifiques d’une ligne de code, par exemple des icônes de tournevis et d’ampoule, des « lignes ondulées » d’erreur et d’avertissement, des signets, etc. Vous pouvez utiliser l’ensemble de commandes « Afficher les annotations de ligne » pour découvrir et parcourir ces ornements.

  ![Utiliser le jeu de commandes Afficher les annotations de ligne](media/show-line-annotations-command-set.png "Capture d’écran de l’élément de menu Afficher les annotations de ligne")

## <a name="access-toolbars-by-using-keyboard-shortcuts"></a>Accéder aux barres d’outils à l’aide de raccourcis clavier

L’IDE Visual Studio possède des barres d’outils comme de nombreuses fenêtres Outil. Les raccourcis clavier suivants vous aident à y accéder.

|Fonctionnalité|Description|Raccourci clavier|
|-------------|-----------------| - |
|Barres d’outils IDE|Sélectionner le premier bouton de la barre d’outils Standard.|**Alt**, **Ctrl**+**Tab**|
|Barres d’outils des fenêtres Outil|Déplacer le focus sur les barres d’outils dans une fenêtre Outil. <br> <br> **REMARQUE :** Cela fonctionne pour la plupart des fenêtres Outil, mais uniquement quand le focus se trouve dans une fenêtre Outil. En outre, vous devez choisir la touche Maj avant la touche Alt. Dans certaines fenêtres Outil, comme Team Explorer, vous devez maintenir la touche Maj enfoncée pendant un moment avant de choisir la touche Alt.|**Maj**+**Alt**|
|Barres d'outils|Accéder au premier élément dans la barre d’outils suivante (quand une barre d’outils a le focus).|**Ctrl**+**Tab**|

### <a name="other-useful-keyboard-shortcuts"></a>Autres raccourcis clavier utiles

Voici d’autres raccourcis clavier utiles.

|Fonctionnalité|Description|Raccourci clavier|
|-------------|-----------------| - |
|IDE|Activer et désactiver le contraste élevé. <br> <br> **REMARQUE :** Raccourci clavier Windows standard|**Alt gauche**+**Maj gauche**+**Imp. écr**|
|Boîte de dialogue|Cocher ou décocher une case dans une boîte de dialogue. <br> <br> **REMARQUE :** Raccourci clavier Windows standard|**Barre d’espace**|
|Menus contextuels|Ouvrir un menu contextuel (clic droit). <br> <br> **REMARQUE :** Raccourci clavier Windows standard|**Maj**+**F10**|
|Menus|Accéder rapidement à un élément de menu à l’aide de ses touches accélérateur. Choisissez la touche **Alt** suivie des lettres soulignées dans un menu pour activer la commande. Par exemple, pour afficher la boîte de dialogue Ouvrir un projet dans Visual Studio, choisissez **Alt**+**F**+**O**+**P**.  <br><br> **REMARQUE :** Raccourci clavier Windows standard|**Alt** +  **[lettre]**|
|Zone de recherche|Utiliser la fonctionnalité de recherche dans Visual Studio.|**Ctrl**+**Q**|
|Fenêtre Boîte à outils|Se déplacer entre les onglets de la boîte à outils.|**Ctrl**+**Haut**<br /><br /> et<br /><br /> **Ctrl**+**Bas**|
|Fenêtre Boîte à outils|Ajouter un contrôle à partir de la boîte à outils à un formulaire ou un concepteur.|**Entrée**|
|Boîte de dialogue Options : Environnement > Clavier|Supprimer une combinaison de touches entrée dans l’option **Appuyer sur les touches de raccourci**.|**Retour arrière**|
|Fenêtre Outil Notifications|Ouvrez la fenêtre Outil Notifications à l’aide de deux combinaisons de touches de raccourci clavier, l’une après de l’autre. Affichez ensuite une notification en utilisant les touches de direction pour la sélectionner.| **Ctrl**+ **&#92;** , **Ctrl**+**N**|

> [!NOTE]
> Selon vos paramètres actifs ou votre édition, les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles qui sont décrites dans l'aide.

## <a name="access-notifications-by-using-keyboard-shortcuts"></a>Accéder aux notifications à l’aide de raccourcis clavier

Quand une notification apparaît dans l’IDE, voici comment accéder à la fenêtre Notifications à l’aide des raccourcis clavier :

1. À partir de n’importe quel emplacement dans l’IDE, appuyez successivement sur les deux raccourcis clavier suivants : **Ctrl**+ **&#92;** , puis **Ctrl**+**N**.

   La fenêtre **Notifications** s’ouvre.

   ![Fenêtre Outil Notifications dans l’IDE Visual Studio](media/toast-notification.png "Capture d’écran de la fenêtre Notifications dans l’IDE Visual Studio")

1. Utilisez la touche **Tab** ou les touches de direction pour sélectionner une notification.

## <a name="use-the-sound-applet-to-set-build-and-breakpoint-cues"></a>Utiliser l’applet Sound (Son) pour définir des signaux de build et de point d’arrêt

Vous pouvez utiliser l’applet Sound (Son) dans Windows pour affecter un son aux événements de programme Visual Studio. Plus précisément, vous pouvez affecter des sons aux événements de programme suivants :

* Accès à un point d’arrêt
* Build annulée
* Échec de la build
* Build réussie

Voici comment :

1. Dans la zone de **recherche** sur un ordinateur exécutant Windows 10, tapez **Modifier les sons système**.

   ![Zone de recherche dans Windows 10](media/type-here-to-search.png "Capture d’écran de la zone de recherche dans Windows 10")

   (Sinon, si Cortana est activé, dites « Hey Cortana », puis « Modifier les sons système ».)

1. Double-cliquez sur **Modifier les sons système**.

   ![Résultats de la recherche dans Windows 10](media/change-system-sounds.png "Capture d’écran des résultats de la recherche « Modifier les sons système » dans Windows 10")

1. Dans la boîte de dialogue **Sound** (Son), cliquez sur l’onglet **Sons**.

1. Dans **Événements**, faites défiler la liste jusqu’à **Microsoft Visual Studio**, puis sélectionnez les sons à appliquer aux événements de votre choix.

   ![Onglet Sons de l’applet Son dans Windows 10](media/sound-applet.png "Onglet Sons de l’applet Son dans Windows 10")

1. Cliquez sur **OK**.

::: moniker range="vs-2017"

> [!TIP]
> Pour en savoir plus sur les mises à jour relatives à l’accessibilité, consultez le billet de blog [Améliorations apportées à l’accessibilité dans Visual Studio 2017 version 15.3](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/).

::: moniker-end

## <a name="see-also"></a>Voir aussi

* [Fonctionnalités d’accessibilité de Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Guide pratique pour personnaliser des menus et des barres d’outils dans Visual Studio](../../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
* [Personnaliser l’IDE Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
* [Accessibilité (Visual Studio pour Mac)](/visualstudio/mac/accessibility)
* [Accessibilité Microsoft](https://www.microsoft.com/Accessibility)
