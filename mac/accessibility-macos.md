---
title: Utilisation des options d’accessibilité macOS
description: Utilisation des options et des fonctionnalités d’accessibilité macOS, telles que le contraste élevé, la navigation à l’aide du clavier et VoiceOver
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/23/2019
ms.assetid: 598FC25A-6DA3-44BB-B128-AD979E9F86EA
ms.topic: how-to
ms.openlocfilehash: 6796ab12716d1d2f3ec2570c32b410c8360b8a81
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998384"
---
# <a name="accessibility-features-of-macos"></a>Fonctionnalités d’accessibilité de macOS

macOS est un système d’exploitation accessible, avec un certain nombre de fonctionnalités pour aider les utilisateurs à faire varier leurs capacités. Parmi ces fonctionnalités, citons le mode de contraste élevé, la navigation au clavier et VoiceOver (le lecteur d’écran macOS).

## <a name="enable-accessibility-features"></a>Activer les fonctionnalités d’accessibilité

Dans Visual Studio pour Mac, la prise en charge des technologies d’assistance est désactivée par défaut. Pour activer la prise en charge de l’accessibilité :

1. Accédez à **Visual Studio (menu)**  >  **Préférences**  >  **autres**, puis sélectionnez **accessibilité**.

1. Activez la case à cocher **activer l’accessibilité** .

   ![Capture d’écran des préférences d’accessibilité, avec l’option Activer l’accessibilité sélectionnée](media/accessibility-preferences.png)

1. Sélectionnez **redémarrer Visual Studio** pour activer la prise en charge des technologies d’assistance Apple.

Vous pouvez aussi utiliser la ligne de commande pour activer les fonctionnalités d’accessibilité. Pour ce faire, entrez la commande suivante dans le terminal :

```bash
defaults write com.microsoft.visual-studio com.monodevelop.AccessibilityEnabled 1
```

Après avoir modifié ce paramètre à l’aide de la ligne de commande, vous devrez redémarrer Visual Studio.

## <a name="increase-the-contrast-in-macos"></a>Augmenter le contraste dans macOS

Visual Studio pour Mac prend en charge l’augmentation du contraste dans macOS, en augmentant le contraste des éléments d’interface utilisateur et en rendant les plans plus définis. Pour l’activer :

1. Ouvrez **Préférences système**.

1. Accédez à **accessibilité**, puis sélectionnez **Afficher**.

1. Activez la case à cocher **augmenter le contraste** .
