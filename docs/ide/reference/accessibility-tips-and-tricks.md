---
title: Conseils et astuces d’accessibilité pour Visual Studio
description: Découvrez les conseils et astuces qui peuvent faciliter l’utilisation de l’environnement de développement intégré (IDE) Visual Studio pour tout le monde, y compris les personnes présentant un handicap.
ms.date: 09/15/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: 6b491d88-f79e-4686-8841-857624bdcfda
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 90a9ba0da2ee8c77b66d147c9af5fa560f50f3a0
ms.sourcegitcommit: e3d96b20381916bf4772f9db52b22275763bb603
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484132"
---
# <a name="accessibility-tips-and-tricks-for-visual-studio"></a>Conseils et astuces d’accessibilité pour Visual Studio

> [!TIP]
> Pour en savoir plus sur les dernières nouveautés en matière d’accessibilité, consultez le billet de blog [Améliorations apportées à l’accessibilité dans Visual Studio 2017 version 15.3](https://blogs.msdn.microsoft.com/visualstudio/2017/08/14/accessibility-improvements-in-visual-studio-2017-version-15-3/).

Visual Studio inclut des fonctionnalités d’accessibilité intégrées qui sont compatibles avec les lecteurs d’écran et d’autres appareils de technologie d’assistance. Cette rubrique répertorie des combinaisons de touches de raccourci courantes que vous pouvez utiliser pour effectuer des tâches avec le clavier uniquement, et inclut des informations sur l’utilisation de thèmes à contraste élevé pour améliorer la visibilité. Elle vous montre également comment utiliser des annotations pour révéler des informations utiles sur votre code et comment définir des signaux audio pour les événements de build et de point d’arrêt.

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Accessibilité pour Visual Studio pour Mac](/visualstudio/mac/accessibility).

## <a name="save-your-ide-settings"></a>Enregistrer vos paramètres IDE

 Vous pouvez personnaliser votre expérience IDE en enregistrant la disposition de vos fenêtres, le schéma de configuration du clavier et d’autres préférences. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="modify-your-ide-for-high-contrast-viewing"></a>Modifier votre IDE pour un affichage à contraste élevé

Pour certaines personnes, quelques couleurs sont plus difficiles à voir. Si vous souhaitez plus de contraste quand vous codez, mais ne voulez pas utiliser les thèmes « Contraste élevé » classiques, nous proposons désormais un thème « Bleu (contraste supplémentaire) ».

  ![Comparer le thème Bleu et le thème Bleu (contraste supplémentaire)](media/blue-extra-contrast-theme.png)

## <a name="use-annotations-to-reveal-useful-information-about-your-code"></a>Utiliser des annotations pour révéler des informations utiles sur votre code

L’éditeur Visual Studio inclut de nombreux « ornements » de texte, qui vous donnent des informations sur des caractéristiques et des fonctionnalités à des endroits spécifiques d’une ligne de code, par exemple des icônes de tournevis et d’ampoule, des « lignes ondulées » d’erreur et d’avertissement, des signets, etc. Vous pouvez utiliser l’ensemble de commandes « Afficher les annotations de ligne » pour découvrir et parcourir ces ornements.

  ![Utiliser le jeu de commandes Afficher les annotations de ligne](media/show-line-annotations-command-set.png)

## <a name="access-toolbars-by-using-shortcut-key-combinations"></a>Accéder aux barres d’outils à l’aide de combinaisons de touches de raccourci

L’IDE Visual Studio possède des barres d’outils comme de nombreuses fenêtres Outil. Les combinaisons de touches de raccourci suivantes vous aident à y accéder.

|Fonctionnalité|Description|Combinaison de touches|
|-------------|-----------------| - |
|Barres d’outils IDE|Sélectionner le premier bouton de la barre d’outils Standard.|**Alt**, **Ctrl** + **Tab**|
|Barres d’outils des fenêtres Outil|Déplacer le focus sur les barres d’outils dans une fenêtre Outil. <br> <br> **REMARQUE :** Cela fonctionne pour la plupart des fenêtres Outil, mais uniquement quand le focus se trouve dans une fenêtre Outil. En outre, vous devez choisir la touche Maj avant la touche Alt. Dans certaines fenêtres Outil, comme Team Explorer, vous devez maintenir la touche Maj enfoncée pendant un moment avant de choisir la touche Alt.|**Maj** + **Alt**|
|Barres d'outils|Accéder au premier élément dans la barre d’outils suivante (quand une barre d’outils a le focus).|**Ctrl** + **Tab**|

### <a name="other-useful-shortcut-key-combinations"></a>Autres combinaisons de touches de raccourci utiles

Parmi d’autres combinaisons de touches de raccourci utiles figurent les suivantes.

|Fonctionnalité|Description|Combinaison de touches|
|-------------|-----------------| - |
|IDE|Activer et désactiver le contraste élevé. <br> <br> **REMARQUE :** Raccourci Windows standard|**Alt gauche + Maj gauche + Impr. écran**|
|Boîte de dialogue|Cocher ou décocher une case dans une boîte de dialogue. <br> <br> **REMARQUE :** Raccourci Windows standard|**Barre d’espace**|
|Menus contextuels|Ouvrir un menu contextuel (clic droit). <br> <br> **REMARQUE :** Raccourci Windows standard|**Maj** + **F10**|
|Menus|Accéder rapidement à un élément de menu à l’aide de ses touches accélérateur. Choisissez la touche **Alt** suivie par les lettres soulignées dans un menu pour activer la commande. Par exemple, pour afficher la boîte de dialogue Ouvrir un projet dans Visual Studio, choisissez **Alt** + **F** + **O** + **P**.  <br><br> **REMARQUE :** Raccourci Windows standard|**Alt** + **[lettre]**|
|Fenêtre Boîte à outils|Se déplacer entre les onglets de la boîte à outils.|**Ctrl** + **Flèche haut**<br /><br /> et<br /><br /> **Ctrl** + **Flèche bas**|
|Fenêtre Boîte à outils|Ajouter un contrôle à partir de la boîte à outils à un formulaire ou un concepteur.|**Entrée**|
|Clavier, Environnement, boîte de dialogue Options|Supprimer une combinaison de touches entrée dans l’option **Appuyer sur les touches de raccourci**.|**Retour arrière**|

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.

## <a name="use-the-sound-applet-to-set-build-and-breakpoint-cues"></a>Utiliser l’applet Sound (Son) pour définir des signaux de build et de point d’arrêt

Vous pouvez utiliser l’applet Sound (Son) dans Windows pour affecter un son aux événements de programme Visual Studio. Plus précisément, vous pouvez affecter des sons aux événements de programme suivants :

 * Accès à un point d’arrêt
 * Build annulée
 * Échec de la build
 * Build réussie

Voici comment procéder.

1. Dans la zone de **recherche** sur un ordinateur exécutant Windows 10, tapez **Modifier les sons système**.

   ![Zone de recherche dans Windows 10](media/type-here-to-search.png)

   (Sinon, si Cortana est activé, dites « Hey Cortana », puis « Modifier les sons système ».)

2. Double-cliquez sur **Modifier les sons système**.

   ![Résultats de recherche dans Windows 10](media/change-system-sounds.png)

3. Dans la boîte de dialogue **Sound** (Son), cliquez sur l’onglet **Sons**. <br><br>
   Ensuite, dans **Événements**, accédez à **Microsoft Visual Studio**, puis sélectionnez les sons que vous souhaitez appliquer aux événements que vous choisissez.

   ![Onglet Sons de l’applet Son dans Windows 10](media/sound-applet.png)

4. Cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi

* [Fonctionnalités d’accessibilité de Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Guide pratique pour personnaliser des menus et des barres d’outils dans Visual Studio](../../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
* [Personnaliser l’IDE Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
* [Accessibilité Microsoft](https://www.microsoft.com/Accessibility)
* [Accessibilité (Visual Studio pour Mac)](/visualstudio/mac/accessibility)