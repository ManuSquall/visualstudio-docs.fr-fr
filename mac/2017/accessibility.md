---
title: Accessibilité
description: Cet article présente les fonctionnalités d’accessibilité dans Visual Studio pour Mac et explique comment les activer.
author: conceptdev
ms.author: crdun
ms.date: 08/15/2017
ms.assetid: 2C4AAC2E-3B4A-4496-8BE0-1F5A7F81D1CA
ms.openlocfilehash: f90f5fca9d68ed00162fd746ddf291343c8d51f7
ms.sourcegitcommit: da73f7a0cf1795d5d400c0897ae3326191435dd0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2019
ms.locfileid: "58568321"
---
# <a name="accessibility"></a>Accessibilité

En plus des fonctionnalités et utilitaires dans macOS, les fonctionnalités suivantes rendent Visual Studio pour Mac plus accessible aux personnes présentant un handicap :

- Agrandissement du texte dans les panneaux Solution et Éditeur
- Options de taille du texte dans les éditeurs
- Personnalisation des couleurs dans les éditeurs
- Personnalisation des raccourcis clavier
- Exécution du code pour les méthodes et les paramètres

Pour plus d’informations sur les fonctionnalités d’accessibilité dans macOS, consultez le [site web d’Apple](https://www.apple.com/accessibility/mac/).

## <a name="using-accessibility-features-in-visual-studio-for-mac"></a>Utilisation des fonctionnalités d’accessibilité dans Visual Studio pour Mac

Les fonctionnalités d’accessibilité dans Visual Studio pour Mac sont désactivées par défaut. Procédez comme suit pour les activer :

1. Accédez à **Visual Studio > Préférences > Autres > Accessibilité**.

2. Cochez la case **Activer l’accessibilité**, comme illustré dans le diagramme suivant :

    ![Case à cocher Activer l’accessibilité](media/accessibility-image1.png)

3. Appuyez sur le bouton **Redémarrer Visual Studio** pour autoriser l’entrée en vigueur des fonctionnalités d’accessibilité.

Vous pouvez aussi utiliser la ligne de commande pour activer les fonctionnalités d’accessibilité. Pour ce faire, entrez la commande suivante dans le terminal :

```bash
defaults write com.microsoft.visual-studio com.monodevelop.AccessibilityEnabled 1
```

Vous devez redémarrer Visual Studio après avoir activé l’accessibilité.

## <a name="how-to-use-keyboard-navigation"></a>Procédure : Utiliser la navigation au clavier

Vous pouvez activer la navigation au clavier en définissant l’option Accès clavier complet dans **Préférences système > Clavier > Raccourcis** sur **Tous les contrôles** :

![Panneau des préférences système dans macOS](media/accessibility-image2.png)

La définition de l’accès clavier complet active le rectangle de focus. Vous pouvez ensuite sélectionner des contrôles comme suit :

- Tabulation pour parcourir les contrôles vers l’avant
- Maj-Tabulation pour parcourir les contrôles vers l’arrière
- Touches de direction pour parcourir les contrôles dans le sens des flèches.

Le fait d’appuyer sur la barre d’espace active le contrôle qui a le focus.

## <a name="how-to-enable-and-use-voice-over"></a>Procédure : Activer et utiliser VoiceOver

Appuyez sur **Cmd + F5** pour activer et désactiver VoiceOver

Pour parcourir les commandes de l’interface utilisateur de VoiceOver, utilisez les commandes suivantes :

- Déplacer le curseur VoiceOver entre les contrôles : **Ctrl + Alt + touche de direction gauche / touche de direction droite**

   La fonction VoiceOver lit le nom des contrôles, certains détails les concernant et comment vous pouvez les utiliser.

- Entrer dans des groupes et des contrôles (par exemple, le panneau Solutions, la Boîte à outils et d’autres panneaux) : **Ctrl + Alt + Maj + flèche vers le bas**

   Une fois à l’intérieur d’un contrôle, vous pouvez utiliser **Ctrl + Alt + flèches** pour vous déplacer.

Pour obtenir des informations générales sur l’utilisation de VoiceOver dans macOS, consultez les guides suivants :

- [Prise en main de VoiceOver](https://help.apple.com/voiceover/info/guide/10.12/)
- [Commandes VoiceOver dans macOS](http://lab.dotjay.com/notes/voiceover-commands/)

## <a name="see-also"></a>Voir aussi

- [Fonctionnalités d’accessibilité de Visual Studio (sur Windows)](/visualstudio/ide/reference/accessibility-features-of-visual-studio)