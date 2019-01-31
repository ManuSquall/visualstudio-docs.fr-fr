---
title: Installer Dotfuscator Community Edition (CE)
ms.date: 06/22/2017
ms.devlang: dotnet
ms.prod: visual-studio-dev15
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protection, community edition, obfuscation, .NET, gratuit, Visual Studio 2017, installer
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
- Dotfuscator installer
- Dotfuscator setup
- install Dotfuscator
- installing Dotfuscator
- set up Dotfuscator
description: Apprenez à installer la version gratuite de Dotfuscator Community Edition incluse dans Visual Studio 2017.
ms.assetid: f2146651-e24a-4e24-ade8-8ddee8ff4e43
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1ce5d7204eaa93fe63fc9ffa49e7ef422d028e76
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54988166"
---
# <a name="install-dotfuscator-community-edition-ce"></a>Installer Dotfuscator Community Edition (CE)

Visual Studio 2017 introduit une nouvelle expérience d’installation à faible impact.
Ainsi, Dotfuscator Community Edition (Dotfuscator CE) n’est pas installé par défaut.
Toutefois, il est facile d’installer Dotfuscator CE même si vous avez déjà installé Visual Studio.

> [!NOTE]
> En plus des versions de Dotfuscator CE fournies avec les versions de Visual Studio, PreEmptive Solutions fournit régulièrement des versions mises à jour sur son site web.
> Si vous souhaitez télécharger la **dernière version** directement au lieu d’effectuer l’installation à partir de Visual Studio, **[cliquez ici pour accéder à la page de téléchargements de Dotfuscator][download]**.

## <a name="within-visual-studio"></a>Dans Visual Studio

Vous pouvez installer Dotfuscator CE depuis l’IDE de Visual Studio :

1. Dans la barre de recherche **Lancement rapide** (Ctrl + Q), tapez `dotfuscator`. <br/> <br/> ![Lancement rapide](media/install_from_vs_12.png) <br/> <br/>
2. Dans les résultats de Lancement rapide, sous le titre *Installer*, sélectionnez **Protection PreEmptive - Dotfuscator (Individual Component)** (Protection PreEmptive - Dotfuscator (composant individuel)).
   * Toutefois, si vous voyez, sous le titre *Menus*, **Outils - PreEmptive Protection - Dotfuscator**, Dotfuscator CE est déjà installé. Pour plus de détails sur l’utilisation, consultez la [page de prise en main dans le guide d’utilisation complet de Dotfuscator CE][get-started].
3. Une fenêtre du programme d’installation Visual Studio s’ouvre, préconfigurée pour installer Dotfuscator CE.
   * Vous devrez peut-être fournir des informations d’identification d’administrateur pour continuer.
4. Fermez toutes les instances de l’IDE de Visual Studio. <br/> <br/> ![Cliquez sur Installer.](media/install_from_vs_345.png) <br/> <br/>
5. Dans la fenêtre du programme d’installation de Visual Studio, cliquez sur *Installer*.

Une fois l’installation terminée, vous pouvez commencer à utiliser Dotfuscator CE. Pour plus de détails, consultez la [page de prise en main dans le guide d’utilisation complet de Dotfuscator CE][get-started].

## <a name="during-visual-studio-installation"></a>Pendant l’installation de Visual Studio

Si vous n’avez pas encore installé Visual Studio 2017, vous pouvez obtenir le programme d’installation à partir du [site web de Visual Studio][2017-install].
Quand vous l’exécutez, il affiche les options d’installation de l’édition de Visual Studio sélectionnée.

![Options d’installation](media/install_ui.png)

Vous pouvez ensuite installer Dotfuscator CE en tant que composant individuel de Visual Studio 2017 :

1. Sélectionnez l’onglet **Composants individuels**.
2. Sous *Outils de code*, cochez l’élément *Protection PreEmptive - Dotfuscator*.<br/> <br/> ![Composants individuels](media/install_individually_12.png) <br/> <br/>
3. Le panneau *Résumé* affiche *Protection PreEmptive - Dotfuscator* dans la section *Composants individuels*. <br/> <br/> ![Volet Récapitulatif](media/install_individually_3.png) <br/> <br/>
4. Configurez les paramètres d’installation supplémentaires en fonction de votre environnement.
5. Quand vous êtes prêt à installer Visual Studio, cliquez sur le bouton *Installer*.

Une fois l’installation terminée, vous pouvez commencer à utiliser Dotfuscator CE. Pour plus de détails, consultez la [page de prise en main dans le guide d’utilisation complet de Dotfuscator CE][get-started].

## <a name="see-also"></a>Voir aussi

[This topic in the full Dotfuscator CE User Guide]: https://www.preemptive.com/dotfuscator/ce/docs/help/

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[2017-install]:  https://visualstudio.microsoft.com/downloads/#vs-2017
[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_install.html