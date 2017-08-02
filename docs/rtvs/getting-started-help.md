---
title: "Fenêtre d’aide dans Outils R pour Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 4/26/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef9c04d4-0d5e-405a-842e-8d47fa0e8781
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 6644ea68ae691e8467828ff699245fef4e485971
ms.contentlocale: fr-fr
ms.lasthandoff: 05/12/2017

---


# <a name="help-in-r-tools-for-visual-studio"></a>Aide dans Outil R pour Visual Studio

L’aide R est intégrée directement à la fenêtre interactive de Visual Studio. Chaque fois que vous utilisez la commande `?`, comme dans `?mtcars`, une rubrique d’aide issue de la documentation R s’affiche dans une fenêtre Visual Studio :

![Fenêtre d’aide dans Visual Studio](~/docs/rtvs/media/help-window.png)

> [!Tip]
> À l’instar des autres fenêtres dans Visual Studio, vous pouvez réorganiser et ancrer la fenêtre d’aide comme bon vous semble. Consultez [Personnaliser les dispositions de fenêtres dans Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).
>
> Vous pouvez également ouvrir les résultats de l’aide dans un navigateur en sélectionnant le menu **Outils R > Options** menu et en affectant à la propriété **Navigateur de l’aide R	** la valeur `External`. Consultez [Options](options.md).

Pour lancer une recherche dans l’aide, utilisez la commande `??` et mettez le terme de recherche entre guillemets s’il comprend des espaces :

```R
??"Motor Trend"
```

![Résultats d’une recherche dans l’aide](~/docs/rtvs/media/help-search1.png)

La fenêtre d’aide comprend également un champ d’entrée de recherche qui vous permet de lancer directement des recherches dans la documentation R :

![Résultats d’une recherche dans l’aide effectuée au moyen du champ d’entrée](~/docs/rtvs/media/help-search2.png)

## <a name="integrated-help-lookup"></a>Recherche dans l’aide intégrée

Étant donné que les développeurs recherchent souvent de l’aide sur les noms de fonctions, les jeux de données et d’autres éléments dans la documentation R, Outils R pour Visual Studio leur facilite la tâche en intégrant des fonctions de recherche dans l’éditeur et la fenêtre interactive.

- Appuyez sur F1 pendant une opération de saisie semi-automatique pour générer une liste de rubriques d’aide correspondant à la sous-chaîne.
- Cliquez avec le bouton droit sur un terme de recherche (comme une fonction) et sélectionnez la commande **Aide sur**, ou appuyez sur F1, pour ouvrir la rubrique d’aide de cette fonction. Vous pouvez également appeler **Aide sur** pour n’importe quelle sélection.

    ![Appel de l’aide par le biais du menu contextuel](~/docs/rtvs/media/help-right-click.png)

> [!Tip]
> Pour ouvrir l’aide intégrée dans un navigateur, sélectionnez **Outils R > Options** et affectez à **Navigateur web (F1)** la valeur `External`. Consultez [Options](options.md).

## <a name="integrated-stackoverflow-search"></a>Recherche dans StackOverflow intégrée

Outre la documentation R, les développeurs consultent souvent StackOverflow quand ils écrivent du code. RTVS simplifie également ce processus. Cliquez avec le bouton droit sur un terme ou une sélection et sélectionnez la commande **Rechercher sur le web**, ou appuyez simplement sur Ctrl+F1. S’ouvre alors une fenêtre Visual Studio (ou un navigateur si vous avez changé l’option **Navigateur web (F1)**) où sont présentés, par défaut, les résultats de la recherche dans StackOverflow :

![Résultats d’une recherche web dans Visual Studio](~/docs/rtvs/media/help-web-search-results.png)

Vous pouvez modifier la chaîne ajoutée, `R site:stackoverflow`, à l’aide de l’option **Outils R > Options > Chaîne de recherche web (F1)** :

![Changement de l’option de chaîne de recherche web (F1)](~/docs/rtvs/media/options-dialog.png)
