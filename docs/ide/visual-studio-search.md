---
title: Utiliser la Recherche Visual Studio
description: Apprenez à utiliser la recherche Visual Studio pour rechercher des paramètres, des menus et du code.
ms.date: 10/08/2020
ms.topic: how-to
helpviewer_keywords:
- environments [Visual Studio], navigation
- documents [Visual Studio], navigating
- IDE, navigation
- navigation [Visual Studio]
- files [Visual Studio], navigating between
- windows [Visual Studio], navigating
- Window.QuickLaunch
- IDE navigator
ms.assetid: 3870a8fd-4afa-4f1e-a811-9fdf41a9e82d
monikerRange: vs-2019
author: profexorgeek
ms.author: jusjohns
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 101875b3a600a71c832498d05073187d2cf0b774
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873903"
---
# <a name="use-visual-studio-search"></a>Utiliser la recherche Visual Studio

L’environnement de développement intégré (IDE) de Visual Studio comporte de nombreux menus, options et fonctionnalités, qui peuvent être difficiles à mémoriser. La fonctionnalité de recherche de Visual Studio est une zone de recherche unique qui aide les développeurs à trouver des menus et des options de l’IDE, tout en recherchant également votre code. Que vous soyez familiarisé avec Visual Studio ou un développeur expérimenté, cette fonctionnalité offre un moyen rapide de rechercher dans les fonctionnalités de l’IDE et dans votre code.

Utilisez le  + raccourci clavier Ctrl **Q** pour accéder à la zone de recherche ou cliquez sur la zone de saisie de la recherche Visual Studio, située en regard de la barre de menus par défaut :

:::image type="content" source="media/visual-studio-search-cropped.png" alt-text="Zone de recherche de Visual Studio" lightbox="media/visual-studio-search.png":::

> [!NOTE]
> La commande exécutée par la recherche Visual Studio est `Window.QuickLaunch` et vous pouvez voir cette fonctionnalité appelée recherche rapide ou lancement rapide.

Contrairement à d’autres fonctionnalités de recherche, telles que Rechercher dans les fichiers ou Rechercher des Explorateur de solutions, la recherche dans les résultats de Visual Studio inclut les fonctionnalités IDE, les options de menu, les noms de fichiers, etc. Les sections suivantes décrivent les différents types de résultats que recherche Visual Studio peut trouver.

## <a name="search-menus-options-and-windows"></a>Rechercher dans les menus, les options et les fenêtres

Vous pouvez utiliser la zone de recherche de Visual Studio pour rechercher des paramètres, des options et des éléments de configuration similaires. Par exemple, recherchez *modifier le thème* pour rechercher et ouvrir rapidement la boîte de dialogue qui vous permet de modifier le thème de couleur de Visual Studio, comme indiqué dans la capture d’écran suivante :

:::image type="content" source="media/visual-studio-search-options.png" alt-text="Rechercher dans les paramètres et les options de Visual Studio":::

> [!TIP]
> Dans la plupart des cas, la recherche Visual Studio vous rappelle également le menu, les touches de raccourci et l’emplacement de chaque élément dans les résultats.

Vous pouvez utiliser la zone de recherche de Visual Studio pour rechercher des éléments de menu et des commandes. Par exemple, recherchez *net sol* pour rechercher et exécuter rapidement la commande nettoyer la solution. Les résultats de la recherche proposent également un rappel permettant de trouver cette commande dans les menus, comme illustré dans la capture d’écran suivante :

:::image type="content" source="media/visual-studio-search-menu.png" alt-text="Rechercher dans les commandes et les éléments de menu de Visual Studio":::

Enfin, vous pouvez rechercher des fenêtres ou des panneaux que vous avez peut-être fermés par erreur. Par exemple, recherchez *test* pour rechercher et ouvrir la fenêtre Explorateur de tests :

:::image type="content" source="media/visual-studio-search-window.png" alt-text="Rechercher dans les fenêtres et les volets Visual Studio":::

## <a name="search-files-and-code"></a>Rechercher des fichiers et du code

La recherche Visual Studio recherche également les éléments de nom de fichier, de code, de méthode et autres correspondances dans vos éléments de solution. Dans la capture d’écran suivante, une recherche de *démarque* a trouvé le fichier MarkdownMetaExtractor.cs, la `MarkdownMetaExtractor` classe et deux méthodes dans la solution :

:::image type="content" source="media/visual-studio-search-files.png" alt-text="Rechercher des fichiers avec Visual Studio Search":::

Vous pouvez également effectuer une recherche « casse mixte ». Dans la capture d’écran suivante, une recherche de *FSS* a trouvé un fichier, une classe et une méthode **F****plus Ille****s** canner :

:::image type="content" source="media/visual-studio-search-camel.png" alt-text="Recherche de bosse mixte avec la recherche Visual Studio":::

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](reference/visual-studio-commands.md)