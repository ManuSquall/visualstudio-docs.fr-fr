---
title: Optimiser la vitesse de démarrage de Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing startup time [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c2c31a67ac019435c5131a1ab33600d26c76f32d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501111"
---
# <a name="optimize-visual-studio-startup-time"></a>Optimiser la vitesse de démarrage de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans l’idéal, Visual Studio doit toujours démarrer le plus rapidement possible. Toutefois, les extensions Visual Studio et les fenêtres d’outils ouvertes peuvent affecter la vitesse de démarrage, car elles se chargent automatiquement au démarrage. La fenêtre **Gérer le niveau de performance de Visual Studio** vous permet non seulement de savoir quelles extensions et fonctionnalités affectent la vitesse de démarrage de Visual Studio, mais également de déterminer leur comportement de chargement, afin de mieux contrôler la rapidité de démarrage de Visual Studio.

## <a name="control-startup-behavior"></a>Contrôler le comportement de démarrage

Pour éviter d’allonger les temps de démarrage, Visual Studio « 15 » permet d’éviter le chargement des extensions au démarrage, à l’aide d’une approche de chargement à la demande. Cela signifie que les extensions ne s’ouvrent pas immédiatement au démarrage de Visual Studio, mais plutôt de manière asynchrone en fonction des besoins après le démarrage. En outre, les fenêtres d’outils restées ouvertes dans une session antérieure de Visual Studio pouvant ralentir la vitesse de démarrage, Visual Studio ouvre les fenêtres d’outils de façon plus intelligente pour ne pas affecter la vitesse de démarrage.

Si Visual Studio détecte un démarrage lent, un message s’affiche pour vous signaler l’extension ou la fenêtre d’outils qui en est la cause. Le message fournit également un lien vers la boîte de dialogue **Gérer le niveau de performance de Visual Studio** qui répertorie les fenêtres d’outils et les extensions qui affectent les performances de démarrage. Cette boîte de dialogue vous permet de modifier les paramètres des fenêtres d’outils et des extensions pour améliorer les performances de démarrage.

![Gérer le niveau de performance de Visual Studio - Fenêtre contextuelle](../ide/media/vside-perfdialog-popup.PNG "Gérer le niveau de performance de Visual Studio - Fenêtre contextuelle")

La boîte de dialogue **Gérer le niveau de performance de Visual Studio** comporte deux catégories : **Extensions** et **Fenêtres d’outils**.

### <a name="control-extensions"></a>Extensions de contrôle
Si une extension ralentit le démarrage de Visual Studio, elle apparaît dans la boîte de dialogue **Gérer le niveau de performance de Visual Studio** quand vous choisissez l’un des types d’extension. Si l’impact sur la vitesse de démarrage (indiqué dans la section **Impact**) est trop élevé, vous pouvez choisir de toujours désactiver l’extension au démarrage en choisissant le bouton **Désactiver**. Vous pouvez réactiver l’extension pour les sessions ultérieures à l’aide du Gestionnaire d’extensions ou de la boîte de dialogue Gérer le niveau de performance de Visual Studio.

![Gérer le niveau de performance de Visual Studio - Extensions](../ide/media/vside-perfdialog-extensions.PNG "Gérer le niveau de performance de Visual Studio - Extensions")

En plus des extensions de démarrage, vous pouvez également désactiver les extensions qui se chargent lors du chargement des solutions, ou quand un utilisateur tape au clavier. Choisissez simplement le scénario pour afficher la liste des extensions associées.

### <a name="control-tool-windows"></a>Contrôler les fenêtres d’outils
Si une fenêtre d’outils ralentit le démarrage de Visual Studio, vous pouvez choisir de conserver son comportement par défaut (ce qui ne procure aucun avantage en termes de vitesse de démarrage) ou de remplacer son comportement par l’un des deux suivants :

- **Ne pas afficher la fenêtre au démarrage :** si vous choisissez cette option, la fenêtre d’outils spécifiée est toujours fermée quand vous ouvrez Visual Studio, même si vous l’avez laissé ouverte dans une session précédente. Vous pouvez ouvrir la fenêtre d’outils à partir du menu.
- **Masquer automatiquement la fenêtre au démarrage :** si vous avez laissé une fenêtre d’outils ouverte lors d’une session précédente, cette option réduit le groupe de la fenêtre d’outils au démarrage pour éviter l’initialisation de la fenêtre. C’est un bon choix si vous utilisez souvent une fenêtre d’outils, car elle est quand même disponible mais n’affecte plus la vitesse de démarrage de Visual Studio.

![Gérer le niveau de performance de Visual Studio - Fenêtres d’outils](../ide/media/vside-perfdialog-toolwindows.PNG "Gérer le niveau de performance de Visual Studio - Fenêtres d’outils")

Si vous changez d’avis, vous pouvez rétablir l’une de ces options dans la boîte de dialogue **Gérer le niveau de performance de Visual Studio**. Pour ouvrir la boîte de dialogue **Gérer le niveau de performance de Visual Studio**, dans la barre de menus, choisissez **Aide**, **Gérer le niveau de performance de Visual Studio**.


