---
title: Améliorer la vitesse de démarrage de Visual Studio
ms.date: 11/15/2017
ms.topic: conceptual
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing performance [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.performancecenter
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: b7ba4e3d3a32aa7921d23b8719ec63733b9e239e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31948442"
---
# <a name="optimize-visual-studio-startup-time"></a>Améliorer la vitesse de démarrage de Visual Studio

Visual Studio est conçu pour démarrer aussi rapidement et efficacement que possible. Toutefois, certaines extensions et fenêtres Outil Visual Studio peuvent affecter le temps de démarrage quand elles sont chargées. Vous pouvez contrôler le comportement des extensions et fenêtres Outil lentes dans la boîte de dialogue **Gérer le niveau de performance de Visual Studio**. Vous trouverez des conseils généraux sur l’amélioration des performances sur la page [Conseils et astuces sur les performances dans Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md).

## <a name="startup-behavior"></a>Comportement au démarrage

Pour éviter d’allonger le temps de démarrage, Visual Studio 2017 utilise une approche de chargement _à la demande_ pour charger les extensions. Ce comportement signifie que les extensions ne s’ouvrent pas immédiatement au démarrage de Visual Studio, mais en fonction des besoins. En outre, les fenêtres d’outils restées ouvertes dans une session antérieure de Visual Studio pouvant ralentir la vitesse de démarrage, Visual Studio ouvre les fenêtres d’outils de façon plus intelligente pour ne pas affecter la vitesse de démarrage.

Si Visual Studio détecte un démarrage lent, un message s’affiche pour vous signaler l’extension ou la fenêtre d’outils qui en est la cause. Le message fournit un lien vers la boîte de dialogue **Gérer le niveau de performance de Visual Studio**. Pour accéder à cette boîte de dialogue, choisissez **Aide** > **Gérer le niveau de performance de Visual Studio** dans la barre de menus.

![Fenêtre Gérer le niveau de performance de Visual Studio indiquant « Nous avons constaté que l’extension... ralentit Visual Studio »](../ide/media/vside_perfdialog_popup.png)

La boîte de dialogue répertorie les fenêtres des extensions et outils qui affectent les performances de démarrage. Vous pouvez changer les paramètres des fenêtres Outil et des extensions pour améliorer les performances de démarrage.

## <a name="a-nameextensions-to-change-extension-settings-to-improve-startup-solution-load-and-typing-performance"></a><a name="extensions" />Pour changer les paramètres d’extension afin d’améliorer les performances de démarrage, de chargement de la solution et de la frappe

1. Ouvrez la boîte de dialogue **Gérer le niveau de performance de Visual Studio** en choisissant **Aide** > **Gérer le niveau de performance de Visual Studio** dans la barre de menus.

    Si une extension ralentit le démarrage, le chargement de solution ou la frappe de Visual Studio, elle apparaît dans la boîte de dialogue **Gérer le niveau de performance de Visual Studio** sous **Extensions** > **Démarrage** (ou **Chargement de la solution** ou **Frappe**).

    ![Gérer le niveau de performance de Visual Studio – Affichage Extensions](../ide/media/vside_perfdialog_extensions.png)

2. Choisissez l’extension que vous voulez désactiver, puis le bouton **Désactiver**.

Vous pouvez toujours réactiver l’extension pour les sessions ultérieures à l’aide du **Gestionnaire d’extensions** ou de la boîte de dialogue **Gérer le niveau de performance de Visual Studio**.

## <a name="a-nametool-windows-to-change-tool-window-settings-to-improve-startup-time"></a><a name="tool-windows" />Pour changer les paramètres de la fenêtre Outil afin d’améliorer les temps de démarrage

1. Ouvrez la boîte de dialogue **Gérer le niveau de performance de Visual Studio** en choisissant **Aide** > **Gérer le niveau de performance de Visual Studio** dans la barre de menus.

    Si une fenêtre Outil ralentit le démarrage de Visual Studio, cette fenêtre Outil apparaît dans la boîte de dialogue **Gérer le niveau de performance de Visual Studio** sous **Fenêtres Outil** > **Démarrage**.

2. Choisissez la fenêtre Outil dont vous souhaitez changer le comportement.

3. Choisissez l’une des trois options suivantes :

    - **Utiliser le comportement par défaut :** comportement par défaut de la fenêtre Outil. Laisser cette option sélectionnée n’améliore pas les performances du démarrage.

    - **Ne pas afficher la fenêtre au démarrage :** la fenêtre Outil spécifiée est toujours fermée quand vous ouvrez Visual Studio, même si vous l’avez laissée ouverte dans une session précédente. Vous pouvez ouvrir la fenêtre Outil à partir du menu approprié quand vous en avez besoin.

    - **Masquer automatiquement la fenêtre au démarrage :** si vous avez laissé une fenêtre d’outils ouverte lors d’une session précédente, cette option réduit le groupe de la fenêtre d’outils au démarrage pour éviter l’initialisation de la fenêtre. Cette option est un bon choix si vous utilisez souvent une fenêtre Outils. La fenêtre Outil est toujours disponible, mais elle n’affecte plus le temps de démarrage de Visual Studio.

    ![Gérer le niveau de performance de Visual Studio – Affichage Fenêtres d’outils](../ide/media/vside_perfdialog_toolwindows.png)

> [!NOTE]
> Certaines versions de Visual Studio antérieures à la version 2017 comportaient une fonctionnalité nommée **chargement de solution allégé**. Cette fonctionnalité n’est plus disponible dans Visual Studio 2017 versions 15.5 et ultérieures. dans lesquelles les solutions volumineuses qui contiennent du code managé se chargent beaucoup plus vite qu’avant, même sans utiliser le chargement de solution allégé.

## <a name="see-also"></a>Voir aussi

- [Optimiser les performances de Visual Studio](../ide/optimize-visual-studio-performance.md)
- [Conseils et astuces sur les performances dans Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md)
- [Visual Studio blog - Load solutions faster with Visual Studio 2017 version 15.6](https://blogs.msdn.microsoft.com/visualstudio/2018/04/04/load-solutions-faster-with-visual-studio-2017-version-15-6/)