---
title: "Optimiser la vitesse de démarrage de Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 01/09/2016
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
author: kempb
ms.author: kempb
manager: ghogen
f1_keywords:
- vs.performancecenter
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 27a265dbbb1f9426ba2dd254095c84239bbd0db7
ms.lasthandoff: 03/07/2017

---
# <a name="optimize-visual-studio-startup-time"></a>Optimiser la vitesse de démarrage de Visual Studio
Dans l’idéal, Visual Studio doit toujours démarrer le plus rapidement possible. Toutefois, les extensions Visual Studio et les fenêtres d’outils ouvertes peuvent affecter la vitesse de démarrage, car elles se chargent automatiquement au démarrage. La fenêtre **Gérer le niveau de performance de Visual Studio** vous permet non seulement de savoir quelles extensions et fonctionnalités affectent la vitesse de démarrage de Visual Studio, mais également de déterminer leur comportement de chargement, afin de mieux contrôler la rapidité de démarrage de Visual Studio.

## <a name="control-startup-behavior"></a>Contrôler le comportement de démarrage

Pour éviter d’allonger la durée de démarrage, Visual Studio 2017 évite de charger les extensions au démarrage, grâce à une approche de chargement à la demande. Cela signifie que les extensions ne s’ouvrent pas immédiatement au démarrage de Visual Studio, mais plutôt de manière asynchrone en fonction des besoins après le démarrage. En outre, les fenêtres d’outils restées ouvertes dans une session antérieure de Visual Studio pouvant ralentir la vitesse de démarrage, Visual Studio ouvre les fenêtres d’outils de façon plus intelligente pour ne pas affecter la vitesse de démarrage.

Si Visual Studio détecte un démarrage lent, un message s’affiche pour vous signaler l’extension ou la fenêtre d’outils qui en est la cause. Le message fournit également un lien vers la boîte de dialogue **Gérer le niveau de performance de Visual Studio** qui répertorie les fenêtres d’outils et les extensions qui affectent les performances de démarrage. Cette boîte de dialogue vous permet de modifier les paramètres des fenêtres d’outils et des extensions pour améliorer les performances de démarrage.

![Gérer le niveau de performance de Visual Studio - Fenêtre contextuelle](../ide/media/vside_perfdialog_popup.PNG "Gérer le niveau de performance de Visual Studio - Fenêtre contextuelle")

La boîte de dialogue **Gérer le niveau de performance de Visual Studio** comporte deux catégories : **Extensions** et **Fenêtres d’outils**.

### <a name="control-extensions"></a>Extensions de contrôle
Si une extension ralentit le démarrage de Visual Studio, elle apparaît dans la boîte de dialogue **Gérer le niveau de performance de Visual Studio** quand vous choisissez l’un des types d’extension. Si l’impact sur la vitesse de démarrage (indiqué dans la section **Impact**) est trop élevé, vous pouvez choisir de toujours désactiver l’extension au démarrage en choisissant le bouton **Désactiver**. Vous pouvez réactiver l’extension pour les sessions ultérieures à l’aide du Gestionnaire d’extensions ou de la boîte de dialogue Gérer le niveau de performance de Visual Studio.

![Gérer le niveau de performance de Visual Studio - Extensions](../ide/media/vside_perfdialog_extensions.PNG "Gérer le niveau de performance de Visual Studio - Extensions")

En plus des extensions de démarrage, vous pouvez également désactiver les extensions qui se chargent lors du chargement des solutions, ou quand un utilisateur tape au clavier. Choisissez simplement le scénario pour afficher la liste des extensions associées.

### <a name="control-tool-windows"></a>Contrôler les fenêtres d’outils
Si une fenêtre d’outils ralentit le démarrage de Visual Studio, vous pouvez choisir de conserver son comportement par défaut (ce qui ne procure aucun avantage en termes de vitesse de démarrage) ou de remplacer son comportement par l’un des deux suivants :

- **Ne pas afficher la fenêtre au démarrage :** si vous choisissez cette option, la fenêtre d’outils spécifiée est toujours fermée quand vous ouvrez Visual Studio, même si vous l’avez laissé ouverte dans une session précédente. Vous pouvez ouvrir la fenêtre d’outils à partir du menu.
- **Masquer automatiquement la fenêtre au démarrage :** si vous avez laissé une fenêtre d’outils ouverte lors d’une session précédente, cette option réduit le groupe de la fenêtre d’outils au démarrage pour éviter l’initialisation de la fenêtre. C’est un bon choix si vous utilisez souvent une fenêtre d’outils, car elle est quand même disponible mais n’affecte plus la vitesse de démarrage de Visual Studio.

![Gérer le niveau de performance de Visual Studio - Fenêtres d’outils](../ide/media/vside_perfdialog_toolwindows.PNG "Gérer le niveau de performance de Visual Studio - Fenêtres d’outils")

Si vous changez d’avis, vous pouvez rétablir l’une de ces options dans la boîte de dialogue **Gérer le niveau de performance de Visual Studio**. Pour ouvrir la boîte de dialogue **Gérer le niveau de performance de Visual Studio**, dans la barre de menus, choisissez **Aide**, **Gérer le niveau de performance de Visual Studio**.

## <a name="speed-up-solution-load"></a>Accélérer le chargement de la solution

Visual Studio 2017 propose une nouvelle fonctionnalité appelée **chargement de solution allégé**, qui réduit le temps et la mémoire nécessaires au chargement de grandes solutions dans l’IDE. Si vous avez une solution de grande taille contenant de nombreux projets C#, Visual Basic ou C++, vous observerez sans doute une nette amélioration des performances si vous activez le chargement de solution allégé.

Certaines fonctionnalités de l’IDE n’étant pas entièrement disponibles quand le chargement de solution allégé est activé, cette fonctionnalité est désactivée par défaut. Les sections suivantes vous aideront à décider s’il faut activer cette fonctionnalité.

### <a name="enable-lightweight-solution-load"></a>Activer le chargement de solution allégé

Vous pouvez activer le chargement de solution allégé pour l’IDE dans son ensemble ou pour des solutions spécifiques. Pour activer le chargement de solution allégé pour l’IDE dans son ensemble, accédez à **Outils**, **Options**, puis à la section **Projets et solutions**.

![Options des outils, boîte de dialogue](../ide/media/VSIDE_LightweightSolutionLoad.png)

Pour activer le chargement de solution allégé pour une solution spécifique, choisissez le nœud de solution de niveau supérieur dans l’Explorateur de solutions.  Dans la fenêtre Propriétés, choisissez l’une des valeurs suivantes pour la propriété **Chargement léger**.

- **Activé :** le chargement de solution allégé est activé pour cette solution, quel que soit le paramètre à l’échelle de l’IDE.
- **Désactivé :** le chargement de solution allégé est désactivé pour cette solution, quel que soit le paramètre à l’échelle de l’IDE.
- **Par défaut :** le comportement de chargement de solution allégé est identique à celui à l’échelle de l’IDE.

![Explorateur de solutions](../ide/media/VSIDE_LSL Solution Setting.png)

Quand vous modifiez le paramètre de chargement de solution allégé, la modification prend effet au prochain chargement de la solution. Vous n’avez pas besoin de redémarrer l’IDE.

### <a name="automatically-enable-lightweight-solution-load"></a>Activer automatiquement le chargement de solution allégé

Quand vous ouvrez une solution de grande taille dans Visual Studio 2017, un message contextuel peut s’afficher et vous proposer d’activer le chargement de solution allégé. Ce message s’affiche uniquement pour les solutions contenant plusieurs projets C#, Visual Basic ou C++. Si vous choisissez la commande **Activer**, le chargement de solution allégé est activé uniquement pour cette solution. Le paramètre à l’échelle de l’IDE ne change pas.

![Fenêtre contextuelle](../ide/media/VSIDE_LSL Popup.png)

Vous pouvez désactiver le chargement de solution allégé dans la fenêtre Propriétés de la solution.

### <a name="lightweight-solution-load-limitations"></a>Limitations du chargement de solution allégé
La plupart des fonctionnalités de l’IDE sont entièrement disponibles quand le chargement de solution allégé est activé. Toutefois, certaines fonctionnalités de l’IDE et extensions tierces peuvent ne pas être entièrement compatibles.  Les fonctionnalités suivantes ne fonctionnent pas quand le chargement de solution allégé est activé :

#### <a name="third-party-extensions"></a>Extensions tierces
Certaines extensions peuvent ne pas fonctionner comme prévu quand le chargement de solution allégé est activé.

#### <a name="edit-and-continue"></a>Modifier & Continuer
Modifier & Continuer ne fonctionne pas dans les projets qui ne sont pas chargés quand vous démarrez le débogage. Les fichiers contenus dans un tel projet seront en lecture seule et une erreur sera signalée pour indiquer que le projet n’a pas été chargé si vous tentez d’effectuer une modification.

#### <a name="f-support"></a>Support technique F#
Quand le chargement de solution allégé est activé, les projets F# peuvent ne pas être générés correctement et les symboles ne pas être tous disponibles dans GoTo.

