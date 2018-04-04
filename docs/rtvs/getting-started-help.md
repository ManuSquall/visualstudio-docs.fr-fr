---
title: Fenêtre d’aide dans Outils R pour Visual Studio | Microsoft Docs
description: L’aide R est directement intégrée à la fenêtre interactive de Visual Studio via la commande « ? » .
ms.custom: ''
ms.date: 001/24/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-r
dev_langs:
- R
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: 47201a249ffda20739cee40add02c68e3c2ced8a
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="help-in-r-tools-for-visual-studio"></a>Aide dans Outil R pour Visual Studio

L’aide R est intégrée directement à la fenêtre interactive de Visual Studio. Chaque fois que vous utilisez la commande `?`, comme dans `?mtcars`, une rubrique d’aide issue de la documentation R s’affiche dans une fenêtre Visual Studio :

![Fenêtre d’aide dans Visual Studio](media/help-window.png)

> [!Tip]
> À l’instar des autres fenêtres dans Visual Studio, vous pouvez réorganiser et ancrer la fenêtre d’aide comme bon vous semble. Consultez [Personnaliser les dispositions de fenêtres dans Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).
>
> Pour ouvrir les résultats de l’aide dans un navigateur, sélectionnez le menu **Outils R > Options** et affectez à la propriété **Navigateur de l’aide R** la valeur `External`. Consultez [Options](options-for-r-tools-in-visual-studio.md).

Pour lancer une recherche dans l’aide, utilisez la commande `??` suivie du terme de recherche. Utilisez des guillemets si le terme de recherche contient des espaces :

```R
??"Motor Trend"
```

![Résultats d’une recherche dans l’aide](media/help-search1.png)

La fenêtre d’aide comprend également un champ d’entrée de recherche qui vous permet de lancer directement des recherches dans la documentation R :

![Résultats d’une recherche dans l’aide effectuée au moyen du champ d’entrée](media/help-search2.png)

## <a name="integrated-help-lookup"></a>Recherche dans l’aide intégrée

Les développeurs recherchent souvent de l’aide sur les noms de fonctions, les datasets et d’autres éléments dans la documentation R. Les outils R pour Visual Studio (RTVS) simplifient le processus en intégrant des fonctions de recherche directement dans l’éditeur et les fenêtres interactives.

- Appuyez sur F1 pendant une opération de saisie semi-automatique pour générer une liste de rubriques d’aide correspondant à la sous-chaîne.
- Cliquez avec le bouton droit sur un terme de recherche (comme une fonction) et sélectionnez la commande **Aide sur** pour ouvrir la rubrique d’aide de cette fonction. Vous pouvez également appeler **Aide sur** pour n’importe quelle sélection.

    ![Appel de l’aide par le biais du menu contextuel](media/help-right-click.png)

> [!Tip]
> Pour ouvrir l’aide intégrée dans un navigateur, sélectionnez **Outils R > Options** et affectez à **Navigateur web (F1)** la valeur `External`. Consultez [Options](options-for-r-tools-in-visual-studio.md).

## <a name="integrated-stackoverflow-search"></a>Recherche dans StackOverflow intégrée

Outre la documentation R, les développeurs consultent souvent StackOverflow quand ils écrivent du code. RTVS simplifie également ce processus. Cliquez avec le bouton droit sur un terme ou une sélection et sélectionnez la commande **Rechercher sur le web** (Ctrl+F1). Visual Studio ouvre une fenêtre avec les résultats de la recherche limités à StackOverflow :

![Résultats d’une recherche web dans Visual Studio](media/help-web-search-results.png)

Vous pouvez modifier la chaîne de portée ajoutée, `R site:stackoverflow`, à l’aide de l’option **Outils R > Options > Chaîne de recherche web (F1)** :

![Changement de l’option de chaîne de recherche web (F1)](media/options-dialog.png)

Si vous préférez afficher les résultats dans un navigateur, modifiez l’option **Navigateur web (F1)** comme décrit dans [Options](options-for-r-tools-in-visual-studio.md).