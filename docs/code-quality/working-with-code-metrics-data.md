---
title: "Utilisation des données de métriques de Code | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
ms.assetid: 988193ec-b4a3-4e11-b5a1-7334979807d5
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 39d45f5d43819dc418b6378d34a19e6af1d8ee12
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="working-with-code-metrics-data"></a>Utiliser des données de la métrique du code
Le **résultats de la métrique Code** fenêtre affiche les données qui sont générées par l’analyse des métriques du code. Pour plus d’informations sur les valeurs de données de métriques de code, consultez [les valeurs de métrique de Code](../code-quality/code-metrics-values.md).  
  
 Cette rubrique contient les sections suivantes :  
  
-   [Code Metrics Results Window](../code-quality/working-with-code-metrics-data.md#BKMK_CodeMetricsResultsWindow)  
  
-   [Affichage des résultats des métriques de Code](../code-quality/working-with-code-metrics-data.md#BKMK_DisplayingCodeMetricsResults)  
  
-   [Filtrage des résultats des métriques de Code](../code-quality/working-with-code-metrics-data.md#BKMK_FilteringCodeMetricsResults)  
  
-   [Ajout, la suppression et la réorganisation des colonnes de données](../code-quality/working-with-code-metrics-data.md#BKMK_AddingRemovingandRearrangingDataColumns)  
  
-   [Copie de données dans le Presse-papiers ou dans Excel](../code-quality/working-with-code-metrics-data.md#BKMK_Copying_Data_to_the_Clipboard_or_Excel)  
  
-   [Création d’un élément de travail selon les résultats de métrique du Code](../code-quality/working-with-code-metrics-data.md#BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results)  
  
##  <a name="BKMK_CodeMetricsResultsWindow"></a> Code Metrics Results Window  
 Le **résultats de la métrique Code** fenêtre a une barre d’outils en haut et colonnes à afficher les résultats calculés.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Hiérarchie**|Le **hiérarchie** colonne contient une vue d’arborescence de la hiérarchie de code que vous pouvez développer ou réduire pour afficher le niveau de détail que vous souhaitez. Les colonnes restantes affichent les résultats calculés. Vous pouvez masquer ou réorganiser les colonnes de résultats que vous le souhaitez.|  
|**Facilité de maintenance**|Le **facilité de maintenance** colonne contient une icône en plus du résultat numérique. Une icône verte indique un niveau relativement élevé de facilité de maintenance. Une icône jaune indique un degré modéré de facilité de maintenance. Une icône rouge indique la facilité de maintenance basse et un point chaud potentiel. Ces indicateurs de couleur correspondent aux catégories de gravité utilisées par la règle FxCop AvoidUnmaintainableCode. Cette règle déclenche une erreur si l’indice de maintenabilité est inférieur à 10, un avertissement si l’index est entre 10 et 20 et une erreur ni un avertissement si l’index est supérieur à 20. L’indice de maintenabilité est une synthèse des trois mesures : la complexité cyclomatique, lignes de code et la complexité des calculs. Ses valeurs ne sont pas exprimés en unités.|  
  
##  <a name="BKMK_DisplayingCodeMetricsResults"></a>Affichage des résultats des métriques de Code  
 La fenêtre Résultats des métriques de Code s’affiche automatiquement lorsque vous générez des résultats de la métrique code. Vous pouvez également afficher la fenêtre à tout moment.  
  
#### <a name="to-display-the-code-metrics-results-window"></a>Pour afficher la fenêtre Résultats de la métrique Code  
  
-   Sur le **analyser** menu, cliquez sur **Windows** puis cliquez sur **résultats de la métrique Code**.  
  
     \- ou -  
  
-   Sur le **vue** menu, pointez sur **autres fenêtres** puis cliquez sur **résultats de la métrique Code**.  
  
     La fenêtre Résultats des métriques de Code s’affiche même si elle ne contient aucun résultat.  
  
#### <a name="to-view-code-metrics-details"></a>Pour afficher les détails des métriques de code  
  
-   Si les résultats de la métrique code ont été générés, développez l’arborescence dans le **hiérarchie** colonne.  
  
##  <a name="BKMK_FilteringCodeMetricsResults"></a>Filtrage des résultats des métriques de Code  
 Vous pouvez filtrer les résultats affichés dans le **résultats de la métrique Code** fenêtre à l’aide de la barre d’outils en haut. Par exemple, vous pouvez souhaiter consulter uniquement les résultats qui ont un indice de maintenabilité inférieur à 65.  
  
 Le **filtre** zone de liste déroulante contient les noms des colonnes de résultats. Lorsqu’un filtre est défini, il est ajouté au bas de la liste avec une mise en retrait. La liste peut contenir les dix derniers filtres qui ont été définis.  
  
#### <a name="to-filter-the-code-metrics-results"></a>Pour filtrer les résultats de la métrique du code  
  
1.  À partir de la **filtre** , sélectionnez le nom de colonne.  
  
2.  Dans **Min**, tapez la valeur minimale à afficher.  
  
3.  Dans **Max**, tapez la valeur maximale à afficher.  
  
4.  Cliquez sur le **appliquer le filtre** bouton.  
  
5.  Pour afficher les détails des résultats, développez l’arborescence de la hiérarchie.  
  
##  <a name="BKMK_AddingRemovingandRearrangingDataColumns"></a>Ajout, la suppression et la réorganisation des colonnes de données  
 Vous pouvez ajouter ou supprimer des résultats les colonnes à partir de la **résultats de la métrique Code** fenêtre. En outre, vous pouvez réorganiser les colonnes de résultats afin qu’ils apparaissent dans l’ordre souhaité.  
  
#### <a name="to-remove-a-column"></a>Pour supprimer une colonne  
  
1.  Cliquez sur le **Ajout/Suppression de colonnes** bouton.  
  
     \- ou -  
  
     Avec le bouton droit n’importe quel en-tête de colonne, puis cliquez sur **Ajout/Suppression de colonnes**.  
  
2.  Dans le **Ajout/Suppression de colonnes** boîte de dialogue, désactivez la case à cocher pour la colonne que vous souhaitez supprimer, puis cliquez sur **OK**.  
  
#### <a name="to-add-a-previously-removed-column"></a>Pour ajouter une colonne précédemment supprimée  
  
1.  Cliquez sur le **Ajout/Suppression de colonnes** bouton.  
  
     \- ou -  
  
     Avec le bouton droit n’importe quel en-tête de colonne, puis cliquez sur **Ajout/Suppression de colonnes**.  
  
2.  Dans le **Ajout/Suppression de colonnes** boîte de dialogue, sélectionnez la case à cocher pour la colonne que vous souhaitez ajouter, puis cliquez sur **OK**.  
  
#### <a name="to-rearrange-columns"></a>Pour réorganiser les colonnes  
  
1.  Cliquez sur le **Ajout/Suppression de colonnes** bouton.  
  
     \- ou -  
  
     Avec le bouton droit n’importe quel en-tête de colonne, puis cliquez sur **Ajout/Suppression de colonnes**.  
  
2.  Dans le **Ajout/Suppression de colonnes** boîte de dialogue, sélectionnez la colonne que vous souhaitez déplacer et puis cliquez sur la flèche haut ou la flèche vers le bas.  
  
3.  Lorsque la colonne positionnée où vous le souhaitez, cliquez sur **OK**.  
  
##  <a name="BKMK_Copying_Data_to_the_Clipboard_or_Excel"></a>Copie de données dans le Presse-papiers ou dans Excel  
 Vous pouvez sélectionner et copier la ligne sélectionnée de données de métrique du code dans le Presse-papiers en tant que chaîne de texte qui contienne une ligne pour le nom et la valeur de chaque colonne de données. Vous pouvez également cliquer sur **ouvrir la liste dans Microsoft Excel** pour exporter toutes les résultats de la métrique du code dans une feuille de calcul Excel  
  
##  <a name="BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results"></a>Création d’un élément de travail selon les résultats de métrique du Code  
 Vous pouvez créer un [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] entraîne l’élément de travail qui est basé sur le **résultats de métrique du Code** fenêtre. Lorsque l’élément de travail est créé, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] entre automatiquement un titre dans le **titre** données de métriques de champ et le code sous le **historique** onglet.  
  
 Pour plus d’informations sur la création d’éléments de travail, consultez [créer un élément de travail &#91; redirigé &#93;](http://msdn.microsoft.com/en-us/24b2e064-16ac-4bf0-8de4-98a1f48b8c4b).  
  
#### <a name="to-create-a-work-item-based-on-a-result"></a>Pour créer un élément de travail basé sur un résultat  
  
1.  Cliquez sur le résultat.  
  
2.  Pointez sur **créer un élément de travail**, puis cliquez sur le type d’élément de travail que vous souhaitez créer (**bogue**, **tâche**, et ainsi de suite).  
  
3.  Compléter le formulaire d’élément de travail en renseignant tous les champs obligatoires.  
  
4.  Sur le **fichier** menu, cliquez sur **Enregistrer tout** pour enregistrer l’élément de travail.  
  
#### <a name="to-create-a-bug-based-on-a-result"></a>Pour créer un bogue à partir d’un résultat  
  
1.  Cliquez sur le résultat pour le sélectionner.  
  
2.  Cliquez sur le **créer un élément de travail** bouton.  
  
3.  Compléter le formulaire d’élément de travail en renseignant tous les champs obligatoires.  
  
4.  Sur le **fichier** menu, cliquez sur **Enregistrer tout** pour enregistrer l’élément de travail.  
  
## <a name="see-also"></a>Voir aussi  
 [Mesure de la complexité et la facilité de maintenance du Code managé](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)   
 [Guide pratique pour générer les données de la métrique du code](../code-quality/how-to-generate-code-metrics-data.md)