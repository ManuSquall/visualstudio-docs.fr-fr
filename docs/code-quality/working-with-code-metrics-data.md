---
title: Fenêtre métrique du code
ms.date: 12/12/2017
ms.topic: reference
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bbe2c216a9293ddc8c5c1212957c2987924d14e1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62825069"
---
# <a name="use-the-code-metrics-results-window"></a>Utiliser la fenêtre Résultats des métriques de Code

Le **résultats de la métrique Code** fenêtre affiche les données qui sont générées par l’analyse de métriques de code. Pour plus d’informations sur les valeurs de données de métriques de code, consultez [les valeurs de métriques de Code](../code-quality/code-metrics-values.md).

## <a name="display-code-metrics-results"></a>Afficher les résultats de métriques de code

Le **résultats de la métrique Code** fenêtre s’affiche automatiquement lorsque vous générez des résultats des métriques de code. Vous pouvez également afficher la fenêtre à tout moment.

Vous pouvez afficher la fenêtre des résultats des métriques de Code à l’aide d’une des séquences de menu suivantes :

- Sur le **analyser** menu, choisissez **Windows** > **résultats de la métrique Code**.

- Sur le **vue** menu, choisissez **Windows autres** > **résultats de la métrique Code**.

Le **résultats de la métrique Code** fenêtre s’ouvre, même si elle ne contient aucun résultat.

### <a name="to-view-code-metrics-details"></a>Pour afficher les détails des métriques de code

Si les résultats de la métrique code ont été générés, développez l’arborescence dans le **hiérarchie** colonne.

## <a name="filter-code-metrics-results"></a>Filtrer les résultats de métriques de code

Vous pouvez filtrer les résultats sont affichés dans le **résultats de la métrique Code** fenêtre à l’aide de la barre d’outils en haut. Par exemple, vous souhaiterez peut-être consulter uniquement les résultats qui ont un indice de maintenabilité inférieur à 65.

Le **filtre** zone de liste déroulante contient les noms des colonnes de résultats. Lorsqu’un filtre est défini, il est ajouté au bas de la liste avec une mise en retrait. La liste peut contenir les 10 derniers filtres qui ont été définis.

### <a name="to-filter-the-code-metrics-results"></a>Pour filtrer les résultats de la métrique du code

1. À partir de la **filtre** , sélectionnez le nom de colonne.

2. Dans **Min**, tapez la valeur minimale à afficher.

3. Dans **Max**, tapez la valeur maximale à afficher.

4. Cliquez sur le **appliquer un filtre** bouton.

5. Pour afficher les détails des résultats, développez l’arborescence hiérarchique.

## <a name="add-remove-and-rearrange-data-columns"></a>Ajouter, supprimer et réorganiser des colonnes de données

Vous pouvez ajouter ou supprimer les colonnes de résultats le **résultats de la métrique Code** fenêtre. En outre, vous pouvez réorganiser les colonnes de résultats afin qu’ils apparaissent dans l’ordre que vous souhaitez.

### <a name="add-or-remove-a-column"></a>Ajouter ou supprimer une colonne

1. Cliquez sur le **Ajout/Suppression de colonnes** bouton, ou avec le bouton droit n’importe quel en-tête de colonne, puis cliquez **Ajout/Suppression de colonnes**.

1. Dans le **Ajout/Suppression de colonnes** boîte de dialogue, activez ou désactivez la case à cocher pour la colonne que vous souhaitez ajouter ou supprimer, puis choisissez **OK**.

### <a name="rearrange-columns"></a>Réorganiser les colonnes

1. Cliquez sur le **Ajout/Suppression de colonnes** bouton.

1. Dans le **Ajout/Suppression de colonnes** boîte de dialogue, sélectionnez la colonne que vous souhaitez déplacer, puis choisissez la flèche vers le haut ou la flèche vers le bas.

1. Lorsque la colonne est positionnée où vous le souhaitez, choisissez **OK**.

## <a name="copy-data-to-the-clipboard-or-excel"></a>Copier des données vers le Presse-papiers, ou Excel

Vous pouvez sélectionner et copier une ligne sélectionnée de données de métrique du code dans le Presse-papiers en tant que chaîne de texte qui contient une ligne pour le nom et la valeur de chaque colonne de données. Vous pouvez également cliquer sur **ouvrir la sélection dans Microsoft Excel** pour exporter tous les résultats de métriques de code vers une feuille de calcul Excel.

## <a name="create-a-work-item-based-on-code-metric-results"></a>Créer un élément de travail selon les résultats de métrique du code

Vous pouvez créer un [Azure tableaux](/azure/devops/boards/index?view=vsts) élément de travail qui est basée sur des résultats dans le **Code Metric Results** fenêtre. Lorsque l’élément de travail est créé, Visual Studio insère automatiquement un titre dans le **titre** données de métrique du code et de champ sous la **historique** onglet.

Pour plus d’informations sur les forums Azure des éléments de travail, consultez [des éléments de travail](/azure/devops/boards/work-items/index?view=vsts).

### <a name="to-create-a-work-item-based-on-a-result"></a>Pour créer un élément de travail basé sur un résultat

1. Cliquez sur le résultat.

2. Pointez sur **créer un élément de travail**, puis cliquez sur le type d’élément de travail à créer (**bogue**, **tâche**, et ainsi de suite).

3. Compléter le formulaire d’élément de travail en remplissant dans tous les champs obligatoires.

4. Sur le **fichier** menu, cliquez sur **Enregistrer tout** pour enregistrer l’élément de travail.

### <a name="to-create-a-bug-based-on-a-result"></a>Pour créer un bogue basé sur un résultat

1. Cliquez sur le résultat pour le sélectionner.

2. Cliquez sur le **créer un élément de travail** bouton.

3. Compléter le formulaire d’élément de travail en remplissant dans tous les champs obligatoires.

4. Sur le **fichier** menu, cliquez sur **Enregistrer tout** pour enregistrer l’élément de travail.

## <a name="see-also"></a>Voir aussi

- [Valeurs de métriques de code](../code-quality/code-metrics-values.md)
- [Guide pratique pour Générer des données de métrique du code](../code-quality/how-to-generate-code-metrics-data.md)