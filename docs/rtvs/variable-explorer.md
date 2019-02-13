---
title: Explorateur de variables pour R
description: L’Explorateur de variables dans Visual Studio affiche toutes les variables dans une portée donnée dans la session R active.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 799b7f2789898e0d02d9588f9a3ad7d1e8098a00
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55919038"
---
# <a name="variable-explorer"></a>Explorateur de variables

La fenêtre **Explorateur de variables**, que vous pouvez ouvrir en cliquant sur **Outils R** > **Fenêtres** > **Explorateur de variables** (ou **Ctrl**+**8** si vous avez utilisé **Outils R** > **Paramètres de science des données**), affiche toutes les variables dans une portée donnée dans la session R active. Par exemple, si vous ouvrez l’**Explorateur de variables** et que vous entrez les lignes suivantes dans la [Fenêtre interactive](interactive-repl-for-r-in-visual-studio.md) :

```R
x <- 42
y <- 43
n <- c(1,2,3,5,8,13)
```

La fenêtre **Explorateur de variables** s’affiche comme suit :

![Fenêtre Explorateur de variables dans Visual Studio](media/variable-explorer-window.png)

Si une trame de données R plus complexe est définie dans la session, vous pouvez parcourir les données. Par exemple, après avoir exécuté `cars <- mtcars`, vous pouvez parcourir le jeu de données en développant les différents nœuds dans l’**Explorateur de variables** :

![Vue développée de l’Explorateur de variables](media/variable-explorer-expanded-results.png)

Pour supprimer des variables, cliquez avec le bouton droit et sélectionnez **Supprimer**, ou sélectionnez la variable et appuyez sur la touche **Suppr**.

Vous pouvez également rechercher une observation dans une trame de données à l’aide de la recherche incrémentielle. Tout d’abord, développez les nœuds dans la trame de données dans laquelle vous souhaitez rechercher, puis entrez des termes de recherche dans la zone de recherche.

## <a name="details-table-view"></a>Vue de détails (tableau)

Les données étant souvent sous forme de tableau, vous pouvez afficher n’importe quel type de données complexe sous forme de tableau distinct en sélectionnant l’icône de loupe ou en cliquant avec le bouton droit et en sélectionnant **Afficher les détails**.

![Vue de tableau de l’Explorateur de variables](media/variable-explorer-table-view.png)

Un clic sur un en-tête de colonne permet de trier les données par colonne (alternant entre croissant et décroissant). Le maintien de la touche **Maj** enfoncée tout en cliquant sur des colonnes supplémentaires permet également de les ajouter au tri. Un clic sur une colonne sans appui sur la touche **Maj** rétablit le tri de colonne unique.

L’ordre dans lequel vous cliquez sur les en-têtes de colonnes détermine l’ordre dans lequel le tri est effectué. Par exemple, **Maj**+**clic** sur la colonne **cyl**, puis **Maj**+**clic** sur la colonne **mpg** deux fois pour trier la liste afin d’obtenir les cylindres par ordre croissant et la consommation en miles par gallon par ordre décroissant :

![Vue de tableau du tri des données d’après deux colonnes.](media/variable-explorer-table-view-sorting.png)

L’**Explorateur de variables** et les vues de tableau étant dans des fenêtres distinctes de Visual Studio, vous pouvez les disposer côte-à-côte pour les utiliser comme vous le souhaitez. Pour obtenir des instructions générales, consultez [Personnalisation des dispositions de fenêtres dans Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).

## <a name="open-in-excel-or-other-csv-capable-application"></a>Ouvrir dans Excel (ou autre application compatible CSV)

Pour une manipulation et une analyse approfondies, il est souvent utile d’exporter des variables de session au format CSV. L’exportation est effectuée avec la petite icône Excel (![icône d’exportation Excel](media/variable-explorer-excel-icon.png)) en regard de chaque nœud dans l’**Explorateur de variables**, ou en cliquant avec le bouton droit sur un élément et en sélectionnant **Ouvrir dans l’application CSV**. Quand vous sélectionnez l’icône, les données sont écrites dans un nouveau fichier CSV dans le dossier *%userprofile%\Documents\RTVS_CSV_Exports*, et ce fichier s’ouvre dans l’application associée avec l’extension *.csv*.

## <a name="scopes"></a>Portées

Par défaut, l’**Explorateur de variables** s’ouvre dans la portée globale. Vous pouvez basculer vers une portée de package en sélectionnant un package dans la liste déroulante en haut de la fenêtre.

![Explorateur de variables montrant une portée de package](media/variable-explorer-package-scopes.png)

Vous pouvez également basculer vers une portée de fonction quand vous êtes arrêté à un point d’arrêt dans le débogueur (notez que l’**Explorateur de variables** ne bascule pas automatiquement vers la portée de fonction du code en cours de débogage) :

![Explorateur de variables montrant une trame de données pendant le débogage](media/variable-explorer-as-locals-window.png)

L’**Explorateur de variables** change automatiquement de portée de fonction à mesure que vous parcourez le code dans le débogueur, par exemple pour afficher les variables locales dans une fonction.

## <a name="import-data-into-variable-explorer"></a>Importer des données dans l’Explorateur de variables

Deux commandes de la barre d’outils de l’**Explorateur de variables**, qui sont également accessibles par l’intermédiaire du menu **Outils R** > **Données**, permettent d’importer des jeux de données CSV externes dans votre session R :  **Importer le jeu de données dans la session R à partir d’une URL web** et **Importer le jeu de données dans la session R à partir d’un fichier texte**.

Une fois que vous avez identifié le fichier CSV à importer, Visual Studio affiche une boîte de dialogue **Importer le jeu de données**, dans laquelle figurent des options pour contrôler la manière dont ce fichier de données est analysé (autrement dit, quel est le séparateur de champs et comment gérer les guillemets). Vous pouvez également afficher un aperçu de la trame de données importée et du fichier de données d’origine :

![Boîte de dialogue Importer le jeu de données](media/variable-explorer-import-dataset-dialog.png)
