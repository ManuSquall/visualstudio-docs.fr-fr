---
title: Accessibilité
description: Cet article présente les fonctionnalités d’accessibilité dans Visual Studio pour Mac et explique comment les activer.
author: conceptdev
ms.author: crdun
ms.date: 04/17/2019
ms.assetid: 2C4AAC2E-3B4A-4496-8BE0-1F5A7F81D1CA
ms.openlocfilehash: 383f9fb46341eec78fa2daa59bba31dde89ac437
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62985299"
---
# <a name="accessibility"></a>Accessibilité

Les fonctionnalités d’accessibilité suivantes rendent Visual Studio pour Mac plus accessible aux personnes présentant un handicap :

- Agrandissement du texte dans les panneaux Solution et Éditeur
- Options de taille du texte dans les éditeurs
- Personnalisation des couleurs dans les éditeurs
- Navigation au clavier
- Personnalisation des raccourcis
- Exécution du code pour les méthodes et les paramètres

Outre ces fonctionnalités, Apple fournit un certain nombre d’outils, comme VoiceOver et Dictée, pour aider les utilisateurs ayant des besoins particuliers.

Pour plus d’informations sur les fonctionnalités d’accessibilité dans macOS, consultez le [site web d’Apple](https://www.apple.com/accessibility/mac/).

## <a name="enabling-macos-assistive-technologies-in-visual-studio-for-mac"></a>Activation des technologies d’assistance de macOS dans Visual Studio pour Mac

Par défaut, la prise en charge des technologies d’assistance de macOS est désactivée dans Visual Studio pour Mac. Pour l’activer, procédez comme suit :

1. Accédez à **Visual Studio (menu) > Préférences > Autres > Accessibilité**

2. Cochez la case **Activer l’accessibilité** :

   ![Case à cocher des préférences de l’accessibilité](media/accessibility-preferences.png)

3. Sélectionnez le bouton **Redémarrer Visual Studio** pour redémarrer Visual Studio et activer la prise en charge des technologies d’assistance d’Apple.

## <a name="how-to-use-keyboard-navigation"></a>Procédure : Utiliser la navigation au clavier

La prise en charge de la navigation au clavier est directement intégrée à macOS, mais afin de disposer de l’expérience la plus complète, vous devez définir macOS pour parcourir **Tous les contrôles** :

![Préférences système, clavier, tous les contrôles](media/accessibility-preferences-keyboard.png)

Le fait de définir **Accès clavier complet** sur **Tous les contrôles** vous permet de parcourir tous les contrôles dans une fenêtre ou boîte de dialogue. Vous pouvez ensuite sélectionner des contrôles comme suit :

- Tabulation pour parcourir les contrôles vers l’avant
- Maj-Tabulation pour parcourir les contrôles vers l’arrière
- Touches de direction pour parcourir les contrôles dans le sens des flèches
- Contrôle-Tab en dehors des zones de texte
- Le fait d’appuyer sur la barre d’espace active le contrôle qui a le focus.

## <a name="how-to-enable-and-use-voiceover"></a>Procédure : Activer et utiliser VoiceOver

Pour activer ou désactiver VoiceOver, appuyez sur **&#8984; + F5**

Dans ce guide, les commandes VoiceOver apparaissent sous la forme **VO+ *touche*** où **VO** fait référence au modificateur défini dans l’application **Utilitaire VoiceOver**. Le modificateur par défaut est **Ctrl + Alt**. Par exemple, en fonction de votre modificateur VoiceOver, **VO + M** équivaut à **Ctrl + Alt + M**. Par souci de concision, les touches du curseur sont dénommées **Gauche** et **Droite**, etc.

Pour naviguer dans l’interface utilisateur de Visual Studio pour Mac, utilisez les combinaisons de touches suivantes :

- **VO + Droite / Gauche** : Naviguer entre les éléments de l’interface utilisateur
    - VoiceOver annonce l’étiquette et le type de contrôle, et explique comment interagir avec celui-ci.
- **VO + Maj + Bas / Haut** : Entrer dans un élément ou le quitter
    - Une fois dans un élément, vous pouvez utiliser **VO + Gauche / Droite** pour naviguer dans les éléments qu’il contient.
- **VO + Espace** : Sélectionner un contrôle ou interagir avec celui-ci
- **VO + M** : Interagir avec la barre de menus Visual Studio pour Mac

Pour plus d’informations sur l’utilisation de VoiceOver et pour obtenir une liste complète des commandes, reportez-vous aux guides suivants :

- [Guide de mise en route VoiceOver d’Apple](https://support.apple.com/en-us/guide/voiceover-guide/welcome/web)
- [Commandes VoiceOver dans macOS](http://lab.dotjay.com/notes/voiceover-commands/)

## <a name="see-also"></a>Voir aussi

- [Fonctionnalités d’accessibilité de Visual Studio (sur Windows)](/visualstudio/ide/reference/accessibility-features-of-visual-studio)
