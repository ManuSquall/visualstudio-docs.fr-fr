---
title: Utilisation des données de la métrique du code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
ms.assetid: 988193ec-b4a3-4e11-b5a1-7334979807d5
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c2460b4e8b9e0b9043178989fcf8825815471be
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645708"
---
# <a name="working-with-code-metrics-data"></a>Utiliser des données de la métrique du code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La fenêtre résultats de la **métrique du code** affiche les données générées par l’analyse de la métrique du code. Pour plus d’informations sur les valeurs de données de métrique du code, consultez valeurs de la [métrique du code](../code-quality/code-metrics-values.md).

 Cette rubrique contient les sections suivantes :

- [Code Metrics Results Window](../code-quality/working-with-code-metrics-data.md#BKMK_CodeMetricsResultsWindow)

- [Affichage des résultats de la métrique du code](../code-quality/working-with-code-metrics-data.md#BKMK_DisplayingCodeMetricsResults)

- [Filtrage des résultats de la métrique du code](../code-quality/working-with-code-metrics-data.md#BKMK_FilteringCodeMetricsResults)

- [Ajout, suppression et réorganisation des colonnes de données](../code-quality/working-with-code-metrics-data.md#BKMK_AddingRemovingandRearrangingDataColumns)

- [Copie de données dans le presse-papiers ou Excel](../code-quality/working-with-code-metrics-data.md#BKMK_Copying_Data_to_the_Clipboard_or_Excel)

- [Création d’un élément de travail en fonction des résultats de la métrique du code](../code-quality/working-with-code-metrics-data.md#BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results)

## <a name="BKMK_CodeMetricsResultsWindow"></a> Code Metrics Results Window
 La fenêtre résultats de la **métrique du code** comporte une barre d’outils en haut et des colonnes pour afficher les résultats calculés.

|Colonne|Description|
|------------|-----------------|
|**Hiérarchie**|La colonne **hiérarchie** contient une arborescence de la hiérarchie de code que vous pouvez développer ou réduire pour afficher le niveau de détail souhaité. Les colonnes restantes affichent les résultats calculés. Vous pouvez masquer ou organiser les colonnes de résultats comme vous le souhaitez.|
|**La facilité**|La colonne **maintenabilité** contient une icône en plus du résultat numérique. Une icône verte indique un degré de facilité de maintenance relativement élevé. Une icône jaune indique un degré modéré de maintenabilité. Une icône rouge indique une maintenabilité faible et un problème potentiel. Ces indicateurs de couleur correspondent aux catégories de gravité utilisées par la règle FxCop AvoidUnmaintainableCode. Cette règle déclenche une erreur si l’index de maintenabilité est inférieur à 10, un avertissement si l’index est compris entre 10 et 20, et ni une erreur, ni un avertissement si l’index est supérieur à 20. L’index de maintenabilité est une synthèse de trois mesures : la complexité cyclomatic, les lignes de code et la complexité du calcul. Ses valeurs ne sont pas exprimées en unités.|

## <a name="BKMK_DisplayingCodeMetricsResults"></a>Affichage des résultats de la métrique du code
 La fenêtre résultats de la métrique du code s’affiche automatiquement lorsque vous générez des résultats de métriques du code. Vous pouvez également afficher la fenêtre à tout moment.

#### <a name="to-display-the-code-metrics-results-window"></a>Pour afficher la fenêtre résultats de la métrique du code

- Dans le menu **analyser** , cliquez sur **fenêtres** , puis sur résultats de la **métrique du code**.

     \- ou -

- Dans le menu **affichage** , pointez sur **autres fenêtres** , puis cliquez sur résultats de la **métrique du code**.

     La fenêtre résultats de la métrique du code s’affiche même s’il ne contient aucun résultat.

#### <a name="to-view-code-metrics-details"></a>Pour afficher les détails de la métrique du code

- Si les résultats de la métrique du code ont été générés, développez l’arborescence dans la colonne **hiérarchie** .

## <a name="BKMK_FilteringCodeMetricsResults"></a>Filtrage des résultats de la métrique du code
 Vous pouvez filtrer les résultats affichés dans la fenêtre résultats de la **métrique du code** à l’aide de la barre d’outils située en haut. Par exemple, vous souhaiterez peut-être afficher uniquement les résultats qui ont un index de maintenabilité inférieur à 65.

 La zone de liste déroulante **filtre** contient les noms des colonnes de résultats. Lorsqu’un filtre est défini, il est ajouté en bas de la liste avec une mise en retrait. La liste peut contenir les dix derniers filtres qui ont été définis.

#### <a name="to-filter-the-code-metrics-results"></a>Pour filtrer les résultats de la métrique du code

1. Dans la liste **filtre** , sélectionnez le nom de la colonne.

2. Dans **min**, tapez la valeur minimale à afficher.

3. Dans **Max**, tapez la valeur maximale à afficher.

4. Cliquez sur le bouton **appliquer le filtre** .

5. Pour afficher les détails du résultat, développez l’arborescence de la hiérarchie.

## <a name="BKMK_AddingRemovingandRearrangingDataColumns"></a>Ajout, suppression et réorganisation des colonnes de données
 Vous pouvez ajouter ou supprimer des colonnes de résultats dans la fenêtre résultats de la **métrique du code** . En outre, vous pouvez réorganiser les colonnes de résultats afin qu’elles s’affichent dans l’ordre de votre choix.

#### <a name="to-remove-a-column"></a>Pour supprimer une colonne

1. Cliquez sur le bouton **Ajouter/supprimer des colonnes** .

     \- ou -

     Cliquez avec le bouton droit sur n’importe quel en-tête de colonne, puis cliquez sur **Ajouter/supprimer des colonnes**.

2. Dans la boîte de dialogue **Ajouter/supprimer des colonnes** , désactivez la case à cocher de la colonne que vous souhaitez supprimer, puis cliquez sur **OK**.

#### <a name="to-add-a-previously-removed-column"></a>Pour ajouter une colonne supprimée précédemment

1. Cliquez sur le bouton **Ajouter/supprimer des colonnes** .

     \- ou -

     Cliquez avec le bouton droit sur n’importe quel en-tête de colonne, puis cliquez sur **Ajouter/supprimer des colonnes**.

2. Dans la boîte de dialogue **Ajouter/supprimer des colonnes** , activez la case à cocher de la colonne que vous souhaitez ajouter, puis cliquez sur **OK**.

#### <a name="to-rearrange-columns"></a>Pour réorganiser les colonnes

1. Cliquez sur le bouton **Ajouter/supprimer des colonnes** .

     \- ou -

     Cliquez avec le bouton droit sur n’importe quel en-tête de colonne, puis cliquez sur **Ajouter/supprimer des colonnes**.

2. Dans la boîte de dialogue **Ajout/suppression de colonnes** , sélectionnez la colonne que vous souhaitez déplacer, puis cliquez sur la flèche vers le haut ou sur la flèche vers le bas.

3. Lorsque la colonne est positionnée à l’emplacement de votre choix, cliquez sur **OK**.

## <a name="BKMK_Copying_Data_to_the_Clipboard_or_Excel"></a>Copie de données dans le presse-papiers ou Excel
 Vous pouvez sélectionner et copier une ligne sélectionnée de données de métriques du code dans le presse-papiers sous la forme d’une chaîne de texte qui contient une ligne pour le nom et la valeur de chaque colonne de données. Vous pouvez également cliquer sur **ouvrir la liste dans Microsoft Excel** pour exporter tous les résultats de la métrique du code dans une feuille de calcul Excel.

## <a name="BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results"></a>Création d’un élément de travail en fonction des résultats de la métrique du code
 Vous pouvez créer un élément de travail [!INCLUDE[esprfound](../includes/esprfound-md.md)] basé sur les résultats dans la fenêtre résultats de la **métrique du code** . Lorsque l’élément de travail est créé, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] entre automatiquement un titre dans le champ **titre** et les données de métrique du code sous l’onglet **historique** .

 Pour plus d’informations sur la création d’éléments de travail, consultez [créer un &#91;élément de travail&#93;Redirigé](https://msdn.microsoft.com/24b2e064-16ac-4bf0-8de4-98a1f48b8c4b).

#### <a name="to-create-a-work-item-based-on-a-result"></a>Pour créer un élément de travail en fonction d’un résultat

1. Cliquez avec le bouton droit sur le résultat.

2. Pointez sur **créer un élément de travail**, puis cliquez sur le type d’élément de travail que vous souhaitez créer (**bogue**, **tâche**, etc.).

3. Complétez le formulaire d’élément de travail en remplissant tous les champs obligatoires.

4. Dans le menu **fichier** , cliquez sur **enregistrer tout** pour enregistrer l’élément de travail.

#### <a name="to-create-a-bug-based-on-a-result"></a>Pour créer un bogue en fonction d’un résultat

1. Cliquez sur le résultat pour le sélectionner.

2. Cliquez sur le bouton **créer un élément de travail** .

3. Complétez le formulaire d’élément de travail en remplissant tous les champs obligatoires.

4. Dans le menu **fichier** , cliquez sur **enregistrer tout** pour enregistrer l’élément de travail.

## <a name="see-also"></a>Voir aussi
 [Mesure de la complexité et de la facilité de maintenance du code managé](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md) [Comment : générer des données de métriques du code](../code-quality/how-to-generate-code-metrics-data.md)
