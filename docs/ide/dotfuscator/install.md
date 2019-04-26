---
title: Installer Dotfuscator Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protection, community edition, obfuscation, .NET, gratuit, Visual Studio 2017, Visual Studio 2019, Visual Studio, installer
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
- Dotfuscator installer
- Dotfuscator setup
- install Dotfuscator
- installing Dotfuscator
- set up Dotfuscator
description: Découvrez comment installer la copie gratuite de Dotfuscator Community fournie avec Visual Studio.
ms.assetid: f2146651-e24a-4e24-ade8-8ddee8ff4e43
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0a6945713d86c510112992be3fefd2d41280ef14
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62557657"
---
# <a name="install-dotfuscator-community"></a>Installer Dotfuscator Community

Dotfuscator Community est un composant facultatif de Visual Studio.
Ces instructions expliquent comment l’installer.

> [!NOTE]
> En plus des versions de Dotfuscator Community fournies avec les versions de Visual Studio, PreEmptive Solutions fournit régulièrement des versions mises à jour sur son site web.
> Si vous souhaitez télécharger la **dernière version** directement au lieu d’effectuer l’installation à partir de Visual Studio, **[cliquez ici pour accéder à la page de téléchargements de Dotfuscator][download]**.

## <a name="within-visual-studio"></a>Dans Visual Studio

::: moniker range="vs-2019"

Vous pouvez installer Dotfuscator Community depuis l’IDE de Visual Studio :

1. Dans la **Zone de recherche** (Ctrl+Q), tapez `dotfuscator`. <br/> <br/> ![Zone de recherche](media/install_in_vs19_12.png) <br/> <br/>

2. Dans les résultats de recherche affichés, sous le titre *Composants*, sélectionnez **Installer PreEmptive Protection - Dotfuscator**.
   * Toutefois, si vous voyez sous le titre *Menus*, **PreEmptive Protection - Dotfuscator Community**, Dotfuscator Community est déjà installé. Sélectionnez cette option pour [démarrer][get-started].

3. Une fenêtre de Visual Studio Installer s’ouvre, préconfigurée pour installer Dotfuscator Community.
   > [!NOTE]
   > Vous devrez peut-être fournir des informations d’identification d’administrateur pour continuer. 

4. Dans la fenêtre du programme d’installation de Visual Studio, cliquez sur *Installer*. <br/> <br/> ![Cliquez sur Installer](media/install_in_vs19_34.png) <br/> <br/>

::: moniker-end

::: moniker range="vs-2017"

Vous pouvez installer Dotfuscator Community depuis l’IDE de Visual Studio :

1. Dans la barre de recherche **Lancement rapide** (Ctrl + Q), tapez `dotfuscator`. <br/> <br/> ![Lancement rapide](media/install_from_vs_12.png) <br/> <br/>

2. Dans les résultats de Lancement rapide, sous le titre *Installer*, sélectionnez **Protection PreEmptive - Dotfuscator (Individual Component)** (Protection PreEmptive - Dotfuscator (composant individuel)).
   * Toutefois, si vous voyez, sous le titre *Menus*, **Outils - PreEmptive Protection - Dotfuscator**, Dotfuscator CE est déjà installé. Sélectionnez cette option pour [démarrer][get-started].

3. Une fenêtre du programme d’installation Visual Studio s’ouvre, préconfigurée pour installer Dotfuscator CE.
   > [!NOTE] 
   > Vous devrez peut-être fournir des informations d’identification d’administrateur pour continuer.

4. Dans la fenêtre du programme d’installation de Visual Studio, cliquez sur *Installer*. <br/> <br/> ![Cliquez sur Installer](media/install_from_vs_345.png) <br/> <br/>

::: moniker-end

Une fois l’installation terminée, vous pouvez [commencer à utiliser Dotfuscator Community][get-started].

## <a name="during-visual-studio-installation"></a>Pendant l’installation de Visual Studio

Si vous n’avez pas encore installé Visual Studio, vous pouvez obtenir le programme d’installation à partir du [site web de Visual Studio][vs-install].
Quand vous l’exécutez, il affiche les options d’installation de l’édition de Visual Studio sélectionnée.

::: moniker range="vs-2019"

![Options d’installation](media/install_ui.png)

::: moniker-end

::: moniker range="vs-2017"

![Options d’installation](media/install_ui_17.png)

::: moniker-end

Vous pouvez ensuite installer Dotfuscator Community en tant que composant individuel de Visual Studio :

1. Sélectionnez l’onglet **Composants individuels**.
2. Sous *Outils de code*, cochez l’élément *Protection PreEmptive - Dotfuscator*.<br/> <br/> ![Composants individuels](media/install_individually_12.png) <br/> <br/>
3. Le panneau *Résumé* affiche *Protection PreEmptive - Dotfuscator* dans la section *Composants individuels*. <br/> <br/> ![Volet Récapitulatif](media/install_individually_3.png) <br/> <br/>
4. Configurez les paramètres d’installation supplémentaires en fonction de votre environnement.
5. Quand vous êtes prêt à installer Visual Studio, cliquez sur le bouton *Installer*.

Une fois l’installation terminée, vous pouvez commencer à utiliser Dotfuscator Community. Pour des détails, consultez la [page de démarrage du guide complet de l’utilisateur de Dotfuscator Community][get-started].

## <a name="see-also"></a>Voir aussi

[Cette rubrique dans le guide complet de l’utilisateur de Dotfuscator Community](https://www.preemptive.com/dotfuscator/ce/docs/help/)

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[vs-install]:  https://visualstudio.microsoft.com/downloads/
[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_install.html