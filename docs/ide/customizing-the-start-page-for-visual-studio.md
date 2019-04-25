---
title: Changer l’expérience de démarrage
ms.date: 02/01/2017
ms.topic: conceptual
f1_keywords:
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start Page
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c8b31f033b9c04871e57836dd263071d87a24fda
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62824254"
---
# <a name="customize-startup"></a>Personnaliser le démarrage

Vous pouvez personnaliser l’expérience de démarrage de Visual Studio de différentes manières, par exemple en ouvrant votre solution la plus récente ou simplement un environnement de développement vide.

::: moniker range="vs-2017"

Vous pouvez également afficher une page de démarrage personnalisée, qui est une page WAML WPF (Windows Presentation Foundation) qui s'exécute dans une fenêtre d'outil et peut exécuter des commandes internes à Visual Studio.

::: moniker-end

## <a name="to-change-the-startup-item"></a>Pour modifier l’élément de démarrage

1. Dans la barre de menus, choisissez **Outils** > **Options**.

2. Développez **Environnement**, puis choisissez **Démarrage**.

::: moniker range="vs-2017"

3. Dans la liste **Au démarrage**, choisissez l’élément à afficher au démarrage de Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

3. Dans la liste **Au démarrage, ouvrir**, choisissez ce qui doit se produire après le lancement de Visual Studio. Vous avez le choix entre la **Fenêtre Démarrer** (qui vous permet d’ouvrir un projet nouveau ou déjà existant), la **Solution la plus récente** ou un **Environnement vide**.

::: moniker-end

::: moniker range="vs-2017"

## <a name="to-show-a-custom-start-page"></a>Pour afficher une page de démarrage personnalisée

Vous pouvez [créer votre propre page de démarrage personnalisée](../extensibility/creating-a-custom-start-page.md) à l’aide du Kit SDK Visual Studio ou vous pouvez en utiliser une déjà créée par un autre utilisateur. Vous pouvez, par exemples, trouver des pages de démarrage personnalisées dans la [Place de marché Visual Studio](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Start%20Pages&sortBy=Downloads).

Pour installer une page de démarrage personnalisée, ouvrez le fichier *.vsix*, ou effectuez un copier-coller des fichiers de la page de démarrage dans le dossier *%USERPROFILE%\Documents\Visual Studio 2017\StartPages* sur votre ordinateur.

### <a name="to-select-which-custom-start-page-to-display"></a>Pour sélectionner la page de démarrage personnalisée à afficher

1. Dans la barre de menus, choisissez **Outils**>**Options**.

1. Développez **Environnement**, puis choisissez **Démarrage**.

1. Dans la liste **Personnaliser la page de démarrage**, choisissez la page que vous souhaitez.

> [!TIP]
> Si une erreur dans une page de démarrage personnalisée provoque le blocage de Visual Studio, vous pouvez ouvrir Visual Studio en mode sans erreur, puis le configurer pour utiliser la page de démarrage par défaut. Consultez [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Voir aussi

- [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md)

::: moniker-end