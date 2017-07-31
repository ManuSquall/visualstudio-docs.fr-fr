---
title: "Optimiser la vitesse de démarrage de Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 7/20/2017
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
ms.translationtype: HT
ms.sourcegitcommit: c3521e1de25854db012cb91bbe09d9463ecb42c7
ms.openlocfilehash: af1ff0dbeeb30e6b3169c6a94dab8da50085bf20
ms.contentlocale: fr-fr
ms.lasthandoff: 07/21/2017

---

# <a name="optimize-visual-studio-startup-time"></a>Optimiser la vitesse de démarrage de Visual Studio
Dans l’idéal, Visual Studio doit toujours démarrer le plus rapidement possible. Toutefois, les extensions Visual Studio et les fenêtres d’outils ouvertes peuvent affecter la vitesse de démarrage, car elles se chargent automatiquement au démarrage. La fenêtre **Gérer le niveau de performance de Visual Studio** vous permet de consulter les extensions et les fonctionnalités qui affectent la durée de démarrage de Visual Studio et de contrôler le comportement de chargement de ces extensions et fonctionnalités.

## <a name="control-startup-behavior"></a>Contrôler le comportement de démarrage

sPour éviter d’allonger la durée de démarrage, Visual Studio 2017 évite de charger les extensions au démarrage, grâce à une approche de chargement à la demande. Ce comportement signifie que les extensions ne s’ouvrent pas immédiatement au démarrage de Visual Studio, mais en fonction des besoins après le démarrage. En outre, les fenêtres d’outils restées ouvertes dans une session antérieure de Visual Studio pouvant ralentir la vitesse de démarrage, Visual Studio ouvre les fenêtres d’outils de façon plus intelligente pour ne pas affecter la vitesse de démarrage.

Si Visual Studio détecte un démarrage lent, un message s’affiche pour vous signaler l’extension ou la fenêtre d’outils qui en est la cause. Le message fournit également un lien vers la boîte de dialogue **Gérer le niveau de performance de Visual Studio**, que vous pouvez également ouvrir à l’aide de la commande de menu **Aide > Gérer le niveau de performance de Visual Studio**.

![Fenêtre Gérer le niveau de performance de Visual Studio indiquant « Nous avons constaté que l’extension... ralentit Visual Studio »](../ide/media/vside_perfdialog_popup.png)

La boîte de dialogue répertorie les fenêtres des extensions et outils qui affectent les performances de démarrage. Cette boîte de dialogue vous permet de modifier les paramètres des fenêtres d’outils et des extensions pour améliorer les performances de démarrage.

### <a name="change-extension-settings"></a>Modifier les paramètres d’extension

Si une extension ralentit le démarrage de Visual Studio, elle apparaît dans la boîte de dialogue **Gérer le niveau de performance de Visual Studio** quand vous choisissez l’un des types d’extension. La boîte de dialogue affiche les extensions qui affectent les performances de démarrage, lors du chargement d’une solution et lorsque vous tapez dans l’éditeur.

![Gérer le niveau de performance de Visual Studio - Vue des extensions](../ide/media/vside_perfdialog_extensions.png)

Si l’impact sur le démarrage, le chargement d’une solution ou la durée de saisie est trop élevé, désactivez l’extension de ce scénario en sélectionnant le bouton **Désactiver**. Vous pouvez toujours réactiver l’extension pour les sessions ultérieures à l’aide du Gestionnaire d’extensions ou de la boîte de dialogue Gérer le niveau de performance de Visual Studio.

### <a name="change-tool-window-settings"></a>Modifier les paramètres de la fenêtre d’outils

Si une fenêtre d’outils ralentit le démarrage de Visual Studio et que vous souhaitez en modifier l’impact, vous pouvez remplacer son comportement en choisissant l’une de deux options à la place de l’option **Utiliser le comportement par défaut** :

- **Ne pas afficher la fenêtre au démarrage :** la fenêtre d’outils spécifiée est toujours fermée quand vous ouvrez Visual Studio, même si vous l’avez laissé ouverte dans une session précédente. Vous pouvez ouvrir la fenêtre d’outils à partir du menu approprié.
- **Masquer automatiquement la fenêtre au démarrage :** si vous avez laissé une fenêtre d’outils ouverte lors d’une session précédente, cette option réduit le groupe de la fenêtre d’outils au démarrage pour éviter l’initialisation de la fenêtre. C’est un bon choix si vous utilisez souvent une fenêtre d’outils, car elle est quand même disponible mais n’affecte plus la vitesse de démarrage de Visual Studio.

![Gérer le niveau de performance de Visual Studio - Vue des fenêtres d’outils](../ide/media/vside_perfdialog_toolwindows.png)

Vous pouvez revenir à cette boîte de dialogue à tout moment pour modifier le paramètre de n’importe quelle fenêtre d’outils.

## <a name="speed-up-solution-load"></a>Accélérer le chargement de la solution

Visual Studio 2017 prend en charge le **chargement de solution allégé**, qui réduit le temps et la mémoire nécessaires au chargement de grandes solutions dans l’IDE. Si vous avez une solution de grande taille contenant de nombreux projets C#, Visual Basic et/ou C++, vous observerez sans doute une nette amélioration des performances si vous activez le chargement de solution allégé.

Certaines fonctionnalités de l’IDE n’étant pas entièrement disponibles quand le chargement de solution allégé est activé, cette fonctionnalité est désactivée par défaut. Les sections suivantes vous aident à décider s’il faut activer cette fonctionnalité.

### <a name="enable-lightweight-solution-load"></a>Activer le chargement de solution allégé

Vous pouvez activer le chargement de solution allégé pour l’IDE dans son ensemble ou pour des solutions spécifiques.

Pour modifier le paramètre de chargement de solution allégé pour tous les projets et solutions, accédez à **Outils > Options > Projets et solutions > Général** et sélectionnez l’une des trois options de chargement :

![Options des outils, boîte de dialogue](../ide/media/VSIDE_LightweightSolutionLoad.png)

- **Laisser Visual Studio choisir ce qui convient le mieux pour ma solution** : Visual Studio détermine s’il faut appliquer le chargement de solution allégé en analysant chaque solution lorsque vous l’ouvrez. 
- **Activé :** l’option Activer le chargement de solution allégé est activée pour cette solution, quel que soit le paramètre à l’échelle de l’IDE.
- **Désactivé :** le chargement de solution allégé est désactivé pour cette solution, quel que soit le paramètre à l’échelle de l’IDE.

Pour activer le chargement de solution allégé pour une solution spécifique, sélectionnez le nœud de solution de niveau supérieur dans l’Explorateur de solutions. Dans la fenêtre **Propriétés**, choisissez **Par défaut**, **Activé** ou **Désactivé** pour la propriété **Chargement allégé**.

![Explorateur de solutions](../ide/media/VSIDE_LSL Solution Setting.png)

Vous pouvez également cliquer avec le bouton droit sur le nœud de solution de niveau supérieur dans l’Explorateur de solutions et sélectionner **Activer le chargement solution allégé** (si la fonctionnalité est désactivée) ou **Désactiver le chargement de solution allégé** (si la fonctionnalité est activée) :

Quand vous modifiez le paramètre de chargement de solution allégé, la modification prend effet au prochain chargement de la solution. Vous n’avez pas besoin de redémarrer l’IDE.

### <a name="automatically-enable-lightweight-solution-load"></a>Activer automatiquement le chargement de solution allégé

Quand vous ouvrez une solution de grande taille dans Visual Studio 2017, un message contextuel peut s’afficher et vous proposer d’activer le chargement de solution allégé. Ce message s’affiche uniquement pour les solutions contenant plusieurs projets C#, Visual Basic ou C++. Si vous choisissez **Activer**, le chargement de solution allégé est activé uniquement pour cette solution. Le paramètre à l’échelle de l’IDE n’est pas modifié.

![Fenêtre contextuelle](../ide/media/VSIDE_LSL Popup.png)

Vous pouvez désactiver le chargement de solution allégé dans la fenêtre **Propriétés** de la solution.

### <a name="limitations"></a>Limitations

La plupart des fonctionnalités de l’IDE sont entièrement disponibles quand le chargement de solution allégé est activé. Toutefois, certaines fonctionnalités de l’IDE et extensions tierces peuvent ne pas être entièrement compatibles.  Les fonctionnalités suivantes ne fonctionnent pas quand le chargement de solution allégé est activé :

- Certaines extensions tierces peuvent ne pas fonctionner comme prévu quand le chargement de solution allégé est activé.
- Modifier & Continuer ne fonctionne pas dans les projets qui ne sont pas chargés quand vous démarrez le débogage. Les fichiers contenus dans un tel projet sont en lecture seule et une erreur est signalée pour indiquer que le projet n’a pas été chargé si vous tentez d’effectuer une modification.
- Quand le chargement de solution allégé est activé, les projets F# peuvent ne pas être générés correctement et les symboles ne pas être tous disponibles dans GoTo.

