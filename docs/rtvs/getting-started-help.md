---
title: Fenêtre d’aide pour R
description: L’aide R est directement intégrée à la fenêtre interactive de Visual Studio via la commande « ? » .
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: af6c6156b1d88c1d015f7700fc7bed061bbe9a76
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62950591"
---
# <a name="help-in-r-tools-for-visual-studio"></a>Aide dans Outil R pour Visual Studio

L’aide R est intégrée directement à la fenêtre interactive de Visual Studio. Chaque fois que vous utilisez la commande `?`, comme dans `?mtcars`, une rubrique d’aide issue de la documentation R s’affiche dans une fenêtre Visual Studio :

![Fenêtre d’aide dans Visual Studio](media/help-window.png)

> [!Tip]
> À l’instar des autres fenêtres dans Visual Studio, vous pouvez réorganiser et ancrer la fenêtre d’aide comme bon vous semble. Consultez [Personnaliser les dispositions de fenêtres dans Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).
>
> Pour ouvrir les résultats de l’aide dans un navigateur, sélectionnez le menu **Outils R** > **Options** et définissez la propriété **Navigateur de l’aide R** sur `External`. Consultez [Options](options-for-r-tools-in-visual-studio.md).

Pour lancer une recherche dans l’aide, utilisez la commande `??` suivie du terme de recherche. Utilisez des guillemets si le terme de recherche contient des espaces :

```R
??"Motor Trend"
```

![Résultats d’une recherche dans l’aide](media/help-search1.png)

La fenêtre d’aide comprend également un champ d’entrée de recherche qui vous permet de lancer directement des recherches dans la documentation R :

![Résultats d’une recherche dans l’aide effectuée au moyen du champ d’entrée](media/help-search2.png)

## <a name="integrated-help-lookup"></a>Recherche dans l’aide intégrée

Les développeurs recherchent souvent de l’aide sur les noms de fonctions, les datasets et d’autres éléments dans la documentation R. Les outils R pour Visual Studio (RTVS) simplifient le processus en intégrant des fonctions de recherche directement dans l’éditeur et les fenêtres interactives.

- Appuyez sur **F1** pendant une opération de complétion automatique pour générer une liste de rubriques d’aide correspondant à la sous-chaîne.
- Cliquez avec le bouton droit sur un terme de recherche (comme une fonction) et sélectionnez la commande **Aide sur** pour ouvrir la rubrique d’aide de cette fonction. Vous pouvez également appeler **Aide sur** pour n’importe quelle sélection.

    ![Appel de l’aide par le biais du menu contextuel](media/help-right-click.png)

> [!Tip]
> Pour ouvrir l’aide intégrée dans un navigateur, sélectionnez **Outils R** > **Options** et définissez **Navigateur web (F1)** sur `External`. Consultez [Options](options-for-r-tools-in-visual-studio.md).

## <a name="integrated-stackoverflow-search"></a>Recherche dans StackOverflow intégrée

Outre la documentation R, les développeurs consultent souvent StackOverflow quand ils écrivent du code. RTVS simplifie également ce processus. Cliquez avec le bouton droit sur un terme ou une sélection et sélectionnez la commande **Rechercher sur le web** (**Ctrl**+**F1**). Visual Studio ouvre alors une fenêtre avec les résultats de la recherche limités à StackOverflow :

![Résultats d’une recherche web dans Visual Studio](media/help-web-search-results.png)

Vous pouvez modifier la chaîne de délimitation ajoutée, `R site:stackoverflow` via l’option **Outils R** > **Options** > **Chaîne de recherche web (F1)** :

![Changement de l’option de chaîne de recherche web (F1)](media/options-dialog.png)

Si vous préférez afficher les résultats dans un navigateur, modifiez l’option **Navigateur web (F1)** comme décrit dans [Options](options-for-r-tools-in-visual-studio.md).