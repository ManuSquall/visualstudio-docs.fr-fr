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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c01543b290d991a189c0851c64526c9c513068ba
ms.sourcegitcommit: 754133c68ad841f7d7962e0b7a575e133289d8a8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91927976"
---
# <a name="use-the-code-metrics-results-window"></a>Utiliser la fenêtre résultats de la métrique du code

La fenêtre résultats de la **métrique du code** affiche les données générées par l’analyse de la métrique du code. Pour plus d’informations sur les valeurs de données de métrique du code, consultez valeurs de la [métrique du code](../code-quality/code-metrics-values.md).

## <a name="display-code-metrics-results"></a>Afficher les résultats de la métrique du code

La fenêtre résultats de la **métrique du code** s’affiche automatiquement lorsque vous générez des résultats de métriques du code. Vous pouvez également afficher la fenêtre à tout moment.

Vous pouvez afficher la fenêtre résultats de la métrique du code à l’aide de l’une des séquences de menu suivantes :

- Dans le menu **analyser** , choisissez résultats de la métrique du **Windows**  >  **code**Windows.

- Dans le menu **affichage** , choisissez **autres**résultats de la  >  **métrique du code**Windows.

La fenêtre résultats de la **métrique du code** s’ouvre, même si elle ne contient aucun résultat.

### <a name="to-view-code-metrics-details"></a>Pour afficher les détails de la métrique du code

Si les résultats de la métrique du code ont été générés, développez l’arborescence dans la colonne **hiérarchie** .

## <a name="filter-code-metrics-results"></a>Filtrer les résultats de la métrique du code

Vous pouvez filtrer les résultats affichés dans la fenêtre résultats de la **métrique du code** à l’aide de la barre d’outils située en haut. Par exemple, vous souhaiterez peut-être afficher uniquement les résultats qui ont un index de maintenabilité inférieur à 65.

La zone de liste déroulante **filtre** contient les noms des colonnes de résultats. Lorsqu’un filtre est défini, il est ajouté en bas de la liste avec une mise en retrait. La liste peut contenir les 10 derniers filtres qui ont été définis.

### <a name="to-filter-the-code-metrics-results"></a>Pour filtrer les résultats de la métrique du code

1. Dans la liste **filtre** , sélectionnez le nom de la colonne.

2. Dans **min**, tapez la valeur minimale à afficher.

3. Dans **Max**, tapez la valeur maximale à afficher.

4. Cliquez sur le bouton **appliquer le filtre** .

5. Pour afficher les détails du résultat, développez l’arborescence de la hiérarchie.

## <a name="add-remove-and-rearrange-data-columns"></a>Ajouter, supprimer et réorganiser des colonnes de données

Vous pouvez ajouter ou supprimer des colonnes de résultats dans la fenêtre résultats de la **métrique du code** . En outre, vous pouvez réorganiser les colonnes de résultats afin qu’elles s’affichent dans l’ordre de votre choix.

### <a name="add-or-remove-a-column"></a>Ajouter ou supprimer une colonne

1. Cliquez sur le bouton **Ajouter/supprimer des colonnes** , ou cliquez avec le bouton droit sur n’importe quel en-tête de colonne, puis cliquez sur **Ajouter/supprimer des colonnes**.

1. Dans la boîte de dialogue **Ajouter/supprimer des colonnes** , activez ou désactivez la case à cocher de la colonne que vous souhaitez ajouter ou supprimer, puis choisissez **OK**.

### <a name="rearrange-columns"></a>Réorganiser les colonnes

1. Cliquez sur le bouton **Ajouter/supprimer des colonnes** .

1. Dans la boîte de dialogue **Ajout/suppression de colonnes** , sélectionnez la colonne que vous souhaitez déplacer, puis cliquez sur la flèche haut ou la flèche vers le bas.

1. Lorsque la colonne est positionnée à l’emplacement de votre choix, cliquez sur **OK**.

## <a name="copy-data-to-the-clipboard-or-excel"></a>Copier des données dans le presse-papiers ou Excel

Vous pouvez sélectionner et copier une ligne sélectionnée de données de métriques du code dans le presse-papiers sous la forme d’une chaîne de texte qui contient une ligne pour le nom et la valeur de chaque colonne de données. Vous pouvez également cliquer sur **ouvrir la sélection dans Microsoft Excel** pour exporter tous les résultats de la métrique du code dans une feuille de calcul Excel.

## <a name="create-a-work-item-based-on-code-metric-results"></a>Créer un élément de travail en fonction des résultats de la métrique du code

Vous pouvez créer un élément de travail [Azure Boards](/azure/devops/boards/index?view=vsts&preserve-view=true) basé sur les résultats dans la fenêtre résultats de la **métrique du code** . Lorsque l’élément de travail est créé, Visual Studio entre automatiquement un titre dans le champ **titre** et les données de métrique du code sous l’onglet **historique** .

Pour plus d’informations sur Azure Boards éléments de travail, consultez [éléments de travail](/azure/devops/boards/work-items/index?view=vsts&preserve-view=true).

### <a name="to-create-a-work-item-based-on-a-result"></a>Pour créer un élément de travail en fonction d’un résultat

1. Cliquez avec le bouton droit sur le résultat.

2. Pointez sur **créer un élément de travail**, puis cliquez sur le type d’élément de travail que vous souhaitez créer (**bogue**, **tâche**, etc.).

3. Complétez le formulaire d’élément de travail en remplissant tous les champs obligatoires.

4. Dans le menu **fichier** , cliquez sur **enregistrer tout** pour enregistrer l’élément de travail.

### <a name="to-create-a-bug-based-on-a-result"></a>Pour créer un bogue en fonction d’un résultat

1. Cliquez sur le résultat pour le sélectionner.

2. Cliquez sur le bouton **créer un élément de travail** .

3. Complétez le formulaire d’élément de travail en remplissant tous les champs obligatoires.

4. Dans le menu **fichier** , cliquez sur **enregistrer tout** pour enregistrer l’élément de travail.

## <a name="see-also"></a>Voir aussi

- [Valeurs de la métrique du code](../code-quality/code-metrics-values.md)
- [Comment : générer des données de métriques du code](../code-quality/how-to-generate-code-metrics-data.md)
