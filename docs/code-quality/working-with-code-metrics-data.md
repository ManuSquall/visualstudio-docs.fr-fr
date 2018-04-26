---
title: La fenêtre Résultats de la métrique Code dans Visual Studio
ms.date: 12/12/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c5e6fdff99a8fc28e83fe4848fa4f31788cda76f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="using-the-code-metrics-results-window"></a>À l’aide de la fenêtre Résultats des métriques de Code

Le **résultats de la métrique Code** fenêtre affiche les données qui sont générées par l’analyse des métriques du code. Pour plus d’informations sur les valeurs de données de métriques de code, consultez [valeurs de la métrique du Code](../code-quality/code-metrics-values.md).

## <a name="displaying-code-metrics-results"></a>Affichage des résultats des métriques de code

Le **résultats de la métrique Code** fenêtre s’affiche automatiquement lorsque vous générez des résultats de la métrique code. Vous pouvez également afficher la fenêtre à tout moment.

### <a name="to-display-the-code-metrics-results-window"></a>Pour afficher la fenêtre Résultats de la métrique Code

- Sur le **analyser** menu, choisissez **Windows** > **résultats de la métrique Code**.

   \- ou -

- Sur le **vue** menu, choisissez **autres fenêtres** > **résultats de la métrique Code**.

Le **résultats de la métrique Code** fenêtre s’affiche, même si elle ne contient aucun résultat.

### <a name="to-view-code-metrics-details"></a>Pour afficher les détails des métriques de code

Si les résultats de la métrique code ont été générés, développez l’arborescence dans le **hiérarchie** colonne.

## <a name="filtering-code-metrics-results"></a>Filtrage des résultats des métriques de code

Vous pouvez filtrer les résultats affichés dans le **résultats de la métrique Code** fenêtre à l’aide de la barre d’outils en haut. Par exemple, vous pouvez souhaiter consulter uniquement les résultats qui ont un indice de maintenabilité inférieur à 65.

Le **filtre** zone de liste déroulante contient les noms des colonnes de résultats. Lorsqu’un filtre est défini, il est ajouté au bas de la liste avec une mise en retrait. La liste peut contenir les dix derniers filtres qui ont été définis.

### <a name="to-filter-the-code-metrics-results"></a>Pour filtrer les résultats de la métrique du code

1.  À partir de la **filtre** , sélectionnez le nom de colonne.

2.  Dans **Min**, tapez la valeur minimale à afficher.

3.  Dans **Max**, tapez la valeur maximale à afficher.

4.  Cliquez sur le **appliquer le filtre** bouton.

5.  Pour afficher les détails des résultats, développez l’arborescence de la hiérarchie.

## <a name="adding-removing-and-rearranging-data-columns"></a>Ajout, la suppression et la réorganisation des colonnes de données

Vous pouvez ajouter ou supprimer des résultats les colonnes à partir de la **résultats de la métrique Code** fenêtre. En outre, vous pouvez réorganiser les colonnes de résultats afin qu’ils apparaissent dans l’ordre souhaité.

### <a name="to-remove-a-column"></a>Pour supprimer une colonne

1. Cliquez sur le **Ajout/Suppression de colonnes** bouton.

     \- ou - avec le bouton droit n’importe quel en-tête de colonne, puis cliquez **Ajout/Suppression de colonnes**.

1. Dans le **Ajout/Suppression de colonnes** boîte de dialogue, désactivez la case à cocher pour la colonne que vous souhaitez supprimer, puis cliquez sur **OK**.

### <a name="to-add-a-previously-removed-column"></a>Pour ajouter une colonne précédemment supprimée

1. Cliquez sur le **Ajout/Suppression de colonnes** bouton.

     \- ou -

     Avec le bouton droit n’importe quel en-tête de colonne, puis cliquez sur **Ajout/Suppression de colonnes**.

1. Dans le **Ajout/Suppression de colonnes** boîte de dialogue, sélectionnez la case à cocher pour la colonne que vous souhaitez ajouter, puis cliquez sur **OK**.

### <a name="to-rearrange-columns"></a>Pour réorganiser les colonnes

1. Cliquez sur le **Ajout/Suppression de colonnes** bouton.

     \- ou -

     Avec le bouton droit n’importe quel en-tête de colonne, puis cliquez sur **Ajout/Suppression de colonnes**.

1. Dans le **Ajout/Suppression de colonnes** boîte de dialogue, sélectionnez la colonne que vous souhaitez déplacer et puis cliquez sur la flèche haut ou la flèche vers le bas.

1. Lorsque la colonne positionnée où vous le souhaitez, cliquez sur **OK**.

## <a name="copying-data-to-the-clipboard-or-excel"></a>Copie de données dans le Presse-papiers ou dans Excel

Vous pouvez sélectionner et copier la ligne sélectionnée de données de métrique du code dans le Presse-papiers en tant que chaîne de texte qui contienne une ligne pour le nom et la valeur de chaque colonne de données. Vous pouvez également cliquer sur **ouvrir la sélection dans Microsoft Excel** pour exporter toutes les résultats de la métrique du code dans une feuille de calcul Excel.

## <a name="creating-a-work-item-based-on-code-metric-results"></a>Création d’un élément de travail selon les résultats de métrique du code

Vous pouvez créer un [Visual Studio Team Services (VSTS)](/vsts/index) entraîne l’élément de travail qui est basé sur le **résultats de métrique du Code** fenêtre. Lorsque l’élément de travail est créé, Visual Studio fournit automatiquement un titre dans le **titre** données de métriques de champ et le code sous le **historique** onglet.

Pour plus d’informations sur VSTS des éléments de travail, consultez [(VSTS) d’éléments de travail](/vsts/work/work-items/index).

### <a name="to-create-a-work-item-based-on-a-result"></a>Pour créer un élément de travail basé sur un résultat

1.  Cliquez sur le résultat.

2.  Pointez sur **créer un élément de travail**, puis cliquez sur le type d’élément de travail que vous souhaitez créer (**bogue**, **tâche**, et ainsi de suite).

3.  Compléter le formulaire d’élément de travail en renseignant tous les champs obligatoires.

4.  Sur le **fichier** menu, cliquez sur **Enregistrer tout** pour enregistrer l’élément de travail.

### <a name="to-create-a-bug-based-on-a-result"></a>Pour créer un bogue à partir d’un résultat

1.  Cliquez sur le résultat pour le sélectionner.

2.  Cliquez sur le **créer un élément de travail** bouton.

3.  Compléter le formulaire d’élément de travail en renseignant tous les champs obligatoires.

4.  Sur le **fichier** menu, cliquez sur **Enregistrer tout** pour enregistrer l’élément de travail.

## <a name="see-also"></a>Voir aussi

- [Valeurs de métrique de code](../code-quality/code-metrics-values.md)
- [Comment : générer des données de métrique du code](../code-quality/how-to-generate-code-metrics-data.md)