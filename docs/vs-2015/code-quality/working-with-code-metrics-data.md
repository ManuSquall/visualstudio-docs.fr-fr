---
title: Utilisation des données de métrique du Code | Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b53e6a5c7ce65675037aac8c6fc4812f895d3b7b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703722"
---
# <a name="working-with-code-metrics-data"></a>Utiliser des données de la métrique du code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le **résultats de la métrique Code** fenêtre affiche les données qui sont générées par l’analyse de métriques de code. Pour plus d’informations sur les valeurs de données de métriques de code, consultez [des valeurs de métriques de Code](../code-quality/code-metrics-values.md).  
  
 Cette rubrique contient les sections suivantes :  
  
- [Code Metrics Results Window](../code-quality/working-with-code-metrics-data.md#BKMK_CodeMetricsResultsWindow)  
  
- [Affichage des résultats des métriques de Code](../code-quality/working-with-code-metrics-data.md#BKMK_DisplayingCodeMetricsResults)  
  
- [Filtrer les résultats des métriques de Code](../code-quality/working-with-code-metrics-data.md#BKMK_FilteringCodeMetricsResults)  
  
- [Ajout, la suppression et la réorganisation des colonnes de données](../code-quality/working-with-code-metrics-data.md#BKMK_AddingRemovingandRearrangingDataColumns)  
  
- [Copie de données dans le Presse-papiers ou dans Excel](../code-quality/working-with-code-metrics-data.md#BKMK_Copying_Data_to_the_Clipboard_or_Excel)  
  
- [Création d’un élément de travail selon les résultats de métrique du Code](../code-quality/working-with-code-metrics-data.md#BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results)  
  
## <a name="BKMK_CodeMetricsResultsWindow"></a> Code Metrics Results Window  
 Le **résultats de la métrique Code** fenêtre a une barre d’outils en haut et colonnes à afficher les résultats calculés.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Hiérarchie**|Le **hiérarchie** colonne contient une arborescence de la hiérarchie de code que vous pouvez développer ou réduire pour afficher le niveau de détail que vous souhaitez. Les colonnes restantes affichent les résultats calculés. Vous pouvez masquer ou réorganiser les colonnes de résultats que vous le souhaitez.|  
|**facilité de maintenance**|Le **la facilité de maintenance** colonne contient une icône ainsi que le résultat numérique. Une icône verte indique un niveau relativement élevé de facilité de maintenance. Une icône jaune indique un degré modéré de facilité de maintenance. Une icône rouge indique la facilité de maintenance faible et un point problématique potentiel. Ces indicateurs de couleur correspondent aux catégories de gravité qui sont utilisés par la règle FxCop AvoidUnmaintainableCode. Cette règle déclenche une erreur si l’indice de maintenabilité est inférieur à 10, un avertissement si l’index est entre 10 et 20 et une erreur ni un avertissement si l’index est supérieur à 20. L’indice de maintenabilité est une synthèse de trois indicateurs : complexité cyclomatique, lignes de code et la complexité des calculs. Ses valeurs ne sont pas exprimées en unités.|  
  
## <a name="BKMK_DisplayingCodeMetricsResults"></a> Affichage des résultats des métriques de Code  
 La fenêtre Résultats des métriques de Code s’affiche automatiquement lorsque vous générez des résultats des métriques de code. Vous pouvez également afficher la fenêtre à tout moment.  
  
#### <a name="to-display-the-code-metrics-results-window"></a>Pour afficher la fenêtre Résultats de la métrique Code  
  
- Sur le **analyser** menu, cliquez sur **Windows** puis cliquez sur **résultats de la métrique Code**.  
  
     \- ou -  
  
- Sur le **vue** menu, pointez sur **Windows autres** puis cliquez sur **résultats de la métrique Code**.  
  
     La fenêtre Résultats des métriques de Code s’affiche même lorsqu’il ne contient aucun résultat.  
  
#### <a name="to-view-code-metrics-details"></a>Pour afficher les détails des métriques de code  
  
- Si les résultats de la métrique code ont été générés, développez l’arborescence dans le **hiérarchie** colonne.  
  
## <a name="BKMK_FilteringCodeMetricsResults"></a> Filtrer les résultats des métriques de Code  
 Vous pouvez filtrer les résultats sont affichés dans le **résultats de la métrique Code** fenêtre à l’aide de la barre d’outils en haut. Par exemple, vous souhaiterez peut-être consulter uniquement les résultats qui ont un indice de maintenabilité inférieur à 65.  
  
 Le **filtre** zone de liste déroulante contient les noms des colonnes de résultats. Lorsqu’un filtre est défini, il est ajouté au bas de la liste avec une mise en retrait. La liste peut contenir les dix derniers filtres qui ont été définis.  
  
#### <a name="to-filter-the-code-metrics-results"></a>Pour filtrer les résultats de la métrique du code  
  
1. À partir de la **filtre** , sélectionnez le nom de colonne.  
  
2. Dans **Min**, tapez la valeur minimale à afficher.  
  
3. Dans **Max**, tapez la valeur maximale à afficher.  
  
4. Cliquez sur le **appliquer un filtre** bouton.  
  
5. Pour afficher les détails des résultats, développez l’arborescence hiérarchique.  
  
## <a name="BKMK_AddingRemovingandRearrangingDataColumns"></a> Ajout, la suppression et la réorganisation des colonnes de données  
 Vous pouvez ajouter ou supprimer les colonnes de résultats le **résultats de la métrique Code** fenêtre. En outre, vous pouvez réorganiser les colonnes de résultats afin qu’ils apparaissent dans l’ordre que vous souhaitez.  
  
#### <a name="to-remove-a-column"></a>Pour supprimer une colonne  
  
1. Cliquez sur le **Ajout/Suppression de colonnes** bouton.  
  
     \- ou -  
  
     Avec le bouton droit n’importe quel en-tête de colonne, puis cliquez sur **Ajout/Suppression de colonnes**.  
  
2. Dans le **Ajout/Suppression de colonnes** boîte de dialogue, décochez la case pour la colonne que vous souhaitez supprimer, puis cliquez sur **OK**.  
  
#### <a name="to-add-a-previously-removed-column"></a>Pour ajouter une colonne précédemment supprimée  
  
1. Cliquez sur le **Ajout/Suppression de colonnes** bouton.  
  
     \- ou -  
  
     Avec le bouton droit n’importe quel en-tête de colonne, puis cliquez sur **Ajout/Suppression de colonnes**.  
  
2. Dans le **Ajout/Suppression de colonnes** boîte de dialogue, sélectionnez la case à cocher pour la colonne que vous souhaitez ajouter, puis cliquez sur **OK**.  
  
#### <a name="to-rearrange-columns"></a>Pour réorganiser les colonnes  
  
1. Cliquez sur le **Ajout/Suppression de colonnes** bouton.  
  
     \- ou -  
  
     Avec le bouton droit n’importe quel en-tête de colonne, puis cliquez sur **Ajout/Suppression de colonnes**.  
  
2. Dans le **Ajout/Suppression de colonnes** boîte de dialogue, sélectionnez la colonne que vous souhaitez déplacer, puis cliquez sur la flèche vers le haut ou la flèche vers le bas.  
  
3. Lorsque la colonne est placée où vous le souhaitez, cliquez sur **OK**.  
  
## <a name="BKMK_Copying_Data_to_the_Clipboard_or_Excel"></a> Copie de données dans le Presse-papiers ou dans Excel  
 Vous pouvez sélectionner et copier une ligne sélectionnée de données de métrique du code dans le Presse-papiers en tant que chaîne de texte qui contient une ligne pour le nom et la valeur de chaque colonne de données. Vous pouvez également cliquer sur **ouvrir la liste dans Microsoft Excel** pour exporter tous les résultats de métriques de code vers une feuille de calcul Excel  
  
## <a name="BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results"></a> Création d’un élément de travail selon les résultats de métrique du Code  
 Vous pouvez créer un [!INCLUDE[esprfound](../includes/esprfound-md.md)] élément de travail qui est basée sur des résultats dans le **Code Metric Results** fenêtre. Lorsque l’élément de travail est créé, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] entre automatiquement un titre dans le **titre** données de métrique du code et de champ sous la **historique** onglet.  
  
 Pour plus d’informations sur la création d’éléments de travail, consultez [créer un élément de travail &#91;redirigé&#93;](https://msdn.microsoft.com/24b2e064-16ac-4bf0-8de4-98a1f48b8c4b).  
  
#### <a name="to-create-a-work-item-based-on-a-result"></a>Pour créer un élément de travail basé sur un résultat  
  
1. Cliquez sur le résultat.  
  
2. Pointez sur **créer un élément de travail**, puis cliquez sur le type d’élément de travail à créer (**bogue**, **tâche**, et ainsi de suite).  
  
3. Compléter le formulaire d’élément de travail en remplissant dans tous les champs obligatoires.  
  
4. Sur le **fichier** menu, cliquez sur **Enregistrer tout** pour enregistrer l’élément de travail.  
  
#### <a name="to-create-a-bug-based-on-a-result"></a>Pour créer un bogue basé sur un résultat  
  
1. Cliquez sur le résultat pour le sélectionner.  
  
2. Cliquez sur le **créer un élément de travail** bouton.  
  
3. Compléter le formulaire d’élément de travail en remplissant dans tous les champs obligatoires.  
  
4. Sur le **fichier** menu, cliquez sur **Enregistrer tout** pour enregistrer l’élément de travail.  
  
## <a name="see-also"></a>Voir aussi  
 [Mesure de la complexité et la maintenabilité du Code managé](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)   
 [Guide pratique pour Générer des données de métrique du Code](../code-quality/how-to-generate-code-metrics-data.md)
