---
title: Explorateur de variables dans les Outils R pour Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 4/10/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c669434-40d8-4970-92cc-502a98c8b5ab
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
ms.openlocfilehash: 7a72afdf01a9c1efb389efc893beedfc1eed87c1
ms.contentlocale: fr-fr
ms.lasthandoff: 05/12/2017

---


# <a name="variable-explorer"></a>Explorateur de variables

La fenêtre **Explorateur de variables**, que vous pouvez ouvrir en cliquant sur **Outils R > Fenêtres > Explorateur de variables** (ou Ctrl+8 si vous avez utilisé **Outils R > Paramètres de science des données**), affiche toutes les variables dans une portée donnée dans la session R active. Par exemple, si vous ouvrez l’Explorateur de variables et que vous entrez les lignes suivantes dans la [Fenêtre interactive](interactive-repl.md) :

```R
x <- 42
y <- 43
n <- c(1,2,3,5,8,13)
```
 
La fenêtre Explorateur de variables s’affiche comme suit :

![Fenêtre Explorateur de variables dans Visual Studio](~/docs/rtvs/media/variable-explorer-window.png)

Si une trame de données R plus complexe est définie dans la session, vous pouvez parcourir les données. Par exemple, après avoir exécuté `cars <- mtcars`, vous pouvez parcourir le jeu de données en développant les différents nœuds dans l’Explorateur de variables :
 
![Vue développée de l’Explorateur de variables](~/docs/rtvs/media/variable-explorer-expanded-results.png)
 
Pour supprimer des variables, cliquez avec le bouton droit et sélectionnez **Supprimer**, ou sélectionnez la variable et appuyez sur la touche Suppr.

Vous pouvez également rechercher une observation dans une trame de données à l’aide de la recherche incrémentielle. Tout d’abord, développez les nœuds dans la trame de données dans laquelle vous souhaitez rechercher, puis entrez des termes de recherche dans la zone de recherche.

## <a name="details-table-view"></a>Vue de détails (tableau)

Les données étant souvent sous forme de tableau, vous pouvez afficher n’importe quel type de données complexe sous forme de tableau distinct en sélectionnant l’icône de loupe ou en cliquant avec le bouton droit et en sélectionnant **Afficher les détails**. 

![Vue de tableau de l’Explorateur de variables](~/docs/rtvs/media/variable-explorer-table-view.png)

Un clic sur un en-tête de colonne permet de trier les données par colonne (alternant entre croissant et décroissant). Maintenir la touche Maj enfoncée en cliquant sur des colonnes supplémentaires permet de les ajouter au tri. Un clic sur une colonne sans appui sur la touche Maj rétablit le tri de colonne unique.

L’ordre dans lequel vous cliquez sur les en-têtes de colonnes détermine l’ordre dans lequel le tri est effectué. Par exemple, si vous cliquez sur la colonne **cyl** en maintenant le touche Maj enfoncée, et que vous cliquez ensuite deux fois sur la colonne **mpg** en maintenant le touche Maj enfoncée, la liste est triée d’après la valeur des cylindres (par ordre croissant) et d’après la consommation en miles par gallon (par ordre croissant) :

![Vue de tableau du tri des données d’après deux colonnes.](~/docs/rtvs/media/variable-explorer-table-view-sorting.png)

L’Explorateur de variables et les vues de tableau étant dans des fenêtres distinctes de Visual Studio, vous pouvez les disposer côte-à-côte pour travailler avec elles comme vous le souhaitez. Pour obtenir des instructions générales, consultez [Personnalisation des dispositions de fenêtres dans Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).

## <a name="open-in-excel-or-other-csv-capable-application"></a>Ouvrir dans Excel (ou autre application compatible CSV)

Pour une manipulation et une analyse approfondies, il est souvent utile d’exporter des variables de session au format CSV, ce que vous pouvez faire avec la petite icône Excel (![icône d’exportation Excel](~/docs/rtvs/media/variable-explorer-excel-icon.png)) en regard de chaque nœud dans l’Explorateur de variables, ou en double-cliquant sur un élément et en sélectionnant **Ouvrir dans l’application CSV**. Quand vous sélectionnez l’icône, les données sont écrites dans un nouveau fichier CSV dans le dossier `%userprofile%\Documents\RTVS_CSV_Exports`, et ce fichier s’ouvre dans l’application associée à l’extension `.csv`.

## <a name="scopes"></a>Portées

Par défaut, l’Explorateur de variables s’ouvre dans la portée globale. Vous pouvez basculer vers une portée de package en sélectionnant un package dans la liste déroulante en haut de la fenêtre.

![Explorateur de variables montrant une portée de package](~/docs/rtvs/media/variable-explorer-package-scopes.png)

Vous pouvez également basculer vers une portée de fonction quand vous êtes arrêté à un point d’arrêt dans le débogueur (notez que l’Explorateur de variables ne bascule pas automatiquement vers la portée de fonction du code en cours de débogage) :

![Explorateur de variables montrant une trame de données pendant le débogage](~/docs/rtvs/media/variable-explorer-as-locals-window.png)

L’Explorateur de variables change automatiquement de portée de fonction à mesure que vous parcourez le code dans le débogueur, par exemple pour afficher les variables locales dans une fonction.


## <a name="importing-data-into-variable-explorer"></a>Importation de données dans l’Explorateur de variables

Deux commandes de la barre d’outils de l’Explorateur de variables, qui sont également accessibles par l’intermédiaire du menu **Outils R > Données**, permettent d’importer des jeux de données CSV externes dans votre session R : **Importer le jeu de données dans la session R à partir d’une URL web** et **Importer le jeu de données dans la session R à partir d’un fichier texte**. 

Une fois que vous avez identifié le fichier CSV à importer, les Outils R pour Visual Studio affichent une boîte de dialogue **Importer le jeu de données**, dans laquelle figurent des options pour contrôler la manière dont ce fichier est analysé (autrement dit, quel est le séparateur de champs et comment gérer les guillemets) et où vous pouvez voir un aperçu de la trame de données importée et du fichier de données d’origine :

![Boîte de dialogue Importer le jeu de données](~/docs/rtvs/media/variable-explorer-import-dataset-dialog.png)

