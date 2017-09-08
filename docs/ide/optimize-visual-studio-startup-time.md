---
title: "Optimiser la vitesse de démarrage de Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 8/31/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing startup time [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
caps.latest.revision: 4
author: mikejo
ms.author: mikejo
manager: ghogen
f1_keywords:
- vs.performancecenter
ms.translationtype: HT
ms.sourcegitcommit: 4306111cd49a5299bfa5d4e5e22b212bc7799fe2
ms.openlocfilehash: 8e419de02104d30344b32e28174bd7de41f91677
ms.contentlocale: fr-fr
ms.lasthandoff: 09/06/2017

---

# <a name="optimize-visual-studio-startup-time"></a>Optimiser la vitesse de démarrage de Visual Studio
Dans l’idéal, Visual Studio doit toujours démarrer le plus rapidement possible. Toutefois, les extensions Visual Studio et les fenêtres d’outils ouvertes peuvent affecter la vitesse de démarrage, car elles se chargent automatiquement au démarrage. La fenêtre **Gérer le niveau de performance de Visual Studio** vous permet de consulter les extensions et les fonctionnalités qui affectent la durée de démarrage de Visual Studio et de contrôler le comportement de chargement de ces extensions et fonctionnalités.

Pour obtenir des conseils généraux sur l’amélioration des performances, consultez [Conseils et astuces pour les performances dans Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md).

## <a name="control-startup-behavior"></a>Contrôler le comportement de démarrage

Pour éviter d’allonger la durée de démarrage, Visual Studio 2017 évite de charger les extensions au démarrage, grâce à une approche de chargement à la demande. Ce comportement signifie que les extensions ne s’ouvrent pas immédiatement au démarrage de Visual Studio, mais en fonction des besoins après le démarrage. En outre, les fenêtres d’outils restées ouvertes dans une session antérieure de Visual Studio pouvant ralentir la vitesse de démarrage, Visual Studio ouvre les fenêtres d’outils de façon plus intelligente pour ne pas affecter la vitesse de démarrage.

Si Visual Studio détecte un démarrage lent, un message s’affiche pour vous signaler l’extension ou la fenêtre d’outils qui en est la cause. Le message fournit également un lien vers la boîte de dialogue **Gérer les performances de Visual Studio**. Vous pouvez également ouvrir cette fenêtre à l’aide de la commande de menu **Aide > Gérer les performances de Visual Studio**.

![Fenêtre Gérer le niveau de performance de Visual Studio indiquant « Nous avons constaté que l’extension... ralentit Visual Studio »](../ide/media/vside_perfdialog_popup.png)

La boîte de dialogue répertorie les fenêtres des extensions et outils qui affectent les performances de démarrage. Cette boîte de dialogue vous permet de modifier les paramètres des fenêtres d’outils et des extensions pour améliorer les performances de démarrage.

### <a name="change-extension-settings"></a>Modifier les paramètres d’extension

Si une extension ralentit le démarrage de Visual Studio, elle apparaît dans la boîte de dialogue **Gérer le niveau de performance de Visual Studio** quand vous choisissez l’un des types d’extension. La boîte de dialogue affiche les extensions qui affectent les performances au démarrage, lors du chargement d’une solution et lorsque vous tapez dans l’éditeur.

![Gérer le niveau de performance de Visual Studio - Vue des extensions](../ide/media/vside_perfdialog_extensions.png)

Si l’impact sur le démarrage, le chargement d’une solution ou la durée de saisie est trop élevé, désactivez l’extension de ce scénario en sélectionnant le bouton **Désactiver**. Vous pouvez toujours réactiver l’extension pour les sessions ultérieures à l’aide du Gestionnaire d’extensions ou de la boîte de dialogue Gérer le niveau de performance de Visual Studio.

### <a name="change-tool-window-settings"></a>Modifier les paramètres de la fenêtre d’outils

Si une fenêtre d’outils ralentit le démarrage de Visual Studio et que vous souhaitez en modifier l’impact, vous pouvez remplacer son comportement en choisissant l’une de deux options à la place de l’option **Utiliser le comportement par défaut** :

- **Ne pas afficher la fenêtre au démarrage :** la fenêtre d’outils spécifiée est toujours fermée quand vous ouvrez Visual Studio, même si vous l’avez laissé ouverte dans une session précédente. Vous pouvez ouvrir la fenêtre d’outils à partir du menu approprié.
- **Masquer automatiquement la fenêtre au démarrage :** si vous avez laissé une fenêtre d’outils ouverte lors d’une session précédente, cette option réduit le groupe de la fenêtre d’outils au démarrage pour éviter l’initialisation de la fenêtre. C’est un bon choix si vous utilisez souvent une fenêtre d’outils, car elle est quand même disponible mais n’affecte plus la vitesse de démarrage de Visual Studio.

![Gérer le niveau de performance de Visual Studio - Vue des fenêtres d’outils](../ide/media/vside_perfdialog_toolwindows.png)

Vous pouvez revenir à cette boîte de dialogue à tout moment pour modifier le paramètre de n’importe quelle fenêtre d’outils.

## <a name="speed_up_solution_load"></a>Charger de grandes solutions plus rapidement dans Visual Studio 2017

Visual Studio 2017 introduit une nouvelle fonctionnalité, appelée chargement de solutions allégé, qui réduit le temps et la mémoire nécessaires au chargement de grandes solutions dans l’IDE. Si vous avez une solution de grande taille contenant de nombreux projets C#, Visual Basic ou C++, vous observerez sans doute une nette amélioration des performances si vous activez le chargement de solution allégé. Pour plus d’informations sur les avantages de cette fonctionnalité, consultez la page [Optimiser le chargement de solutions](../ide/optimize-solution-loading-in-visual-studio).

> [!NOTE]
> Ce contenu s’applique à Visual Studio 2017 Update 3.

### <a name="enable-or-disable-lightweight-solution-load"></a>Activer ou désactiver le chargement de solutions allégé

Vous pouvez cliquer avec le bouton droit sur le nom de la solution dans l’Explorateur de solutions, puis sélectionner **Activer le chargement de solutions allégé**. Après avoir sélectionné l’option, vous devez fermer et rouvrir la solution afin d’activer le chargement de solutions allégé.

![Explorateur de solutions](../ide/media/VSIDE_LSL_Solution_Setting.png)

Pour configurer les paramètres globaux du chargement de solutions allégé, consultez la page [Optimiser le chargement de solutions](../ide/optimize-solution-loading-in-visual-studio.md#global_solution_load_settings).

## <a name="see-also"></a>Voir aussi
[Conseils et astuces pour les performances dans Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md)

