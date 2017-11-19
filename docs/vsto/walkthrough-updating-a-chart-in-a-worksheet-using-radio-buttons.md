---
title: "Procédure pas à pas : Mise à jour d’un graphique dans une feuille de calcul à l’aide de cases d’option | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, updating using managed controls
- controls [Office development in Visual Studio], updating worksheets
- worksheets, using radio buttons
ms.assetid: cacc43a3-6d95-4a47-b943-3457d97a16f8
caps.latest.revision: "58"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 74bd005514fa2fe72450a95d84f38dd17a7b639f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons"></a>Procédure pas à pas : mise à jour d'un graphique dans une feuille de calcul à l'aide de cases d'option
  Cette procédure pas à pas illustre les principes fondamentaux de l’utilisation de cases d’option dans une feuille de calcul Microsoft Office Excel pour permettre à l’utilisateur pour basculer rapidement entre les options. Dans ce cas, les options changent le style d’un graphique.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Pour afficher le résultat sous la forme d’un exemple complet, consultez l’exemple des contrôles Excel [exemples de développement Office et des procédures pas à pas](../vsto/office-development-samples-and-walkthroughs.md).  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Ajout d’un groupe de cases d’option à une feuille de calcul.  
  
-   Changement de style de graphique quand une option est sélectionnée.  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="adding-a-chart-to-a-worksheet"></a>Ajout d’un graphique à une feuille de calcul  
 Vous pouvez créer un projet de classeur Excel qui personnalise un classeur existant. Dans cette procédure pas à pas, vous ajoutez un graphique à un classeur et ensuite utiliser ce classeur dans une nouvelle solution Excel. La source de données dans cette procédure pas à pas est une feuille de calcul nommée **les données de graphique**.  
  
#### <a name="to-add-the-data"></a>Pour ajouter les données  
  
1.  Ouvrez Microsoft Excel.  
  
2.  Cliquez sur le **Sheet3** onglet, puis cliquez sur **renommer** dans le menu contextuel.  
  
3.  Renommez la feuille à **les données de graphique**.  
  
4.  Ajoutez les données suivantes pour **les données de graphique** cellule A4 étant le coin supérieur gauche et les E8 l’angle inférieur droit.  
  
    ||Q1|Q2|3E TRIMESTRE|Q4|  
    |-|--------|--------|--------|--------|  
    |Ouest|500|550|550|600|  
    |Est de|600|625|675|700|  
    |Nord|450|470|490|510|  
    |Sud|800|750|775|790|  
  
 Ensuite, ajoutez un graphique à la première feuille de calcul pour afficher les données.  
  
#### <a name="to-add-a-chart-in-excel"></a>Pour ajouter un graphique dans Excel  
  
1.  Sur le **insérer** sous l’onglet du **graphiques** , cliquez sur **colonne**, puis cliquez sur **tous les Types de graphiques**.  
  
2.  Dans le **insérer un graphique** boîte de dialogue, cliquez sur **OK**.  
  
3.  Sur le **conception** sous l’onglet du **données** , cliquez sur **sélectionner les données**.  
  
4.  Dans le **sélectionner une Source de données** boîte de dialogue, cliquez dans le **Chartdata plage** zone, puis désactivez toutes les sélections par défaut.  
  
5.  Dans le **les données de graphique** feuille, sélectionnez la plage de cellules qui contient les nombres incluant A4 dans le coin supérieur gauche pour E8 dans le coin inférieur droit.  
  
6.  Dans le **sélectionner une Source de données** boîte de dialogue, cliquez sur **OK**.  
  
7.  Repositionnez le graphique afin que le coin supérieur droit s’aligne avec la cellule **E2**.  
  
8.  Enregistrez votre fichier sur le lecteur C et nommez-le **ExcelChart.xlsx**.  
  
9. Quittez Excel.  
  
## <a name="creating-a-new-project"></a>Création d'un projet  
 Dans cette étape, vous allez créer un projet de classeur Excel basé sur le **ExcelChart** classeur.  
  
#### <a name="to-create-a-new-project"></a>Pour créer un projet  
  
1.  Créer un projet de classeur Excel portant le nom **mon graphique Excel**. Dans l’Assistant, sélectionnez **copier un document existant**.  
  
     Pour plus d'informations, consultez [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Cliquez sur le **Parcourir** buttonand recherchez le classeur que vous avez créé précédemment dans cette procédure pas à pas.  
  
3.  Cliquez sur **OK**.  
  
     Visual Studio ouvre le nouveau classeur Excel dans le concepteur et ajoute le **mon graphique Excel** projet **l’Explorateur de solutions**.  
  
## <a name="setting-properties-of-the-chart"></a>Définition des propriétés du graphique  
 Lorsque vous créez un nouveau projet de classeur Excel qui utilise un classeur existant, les contrôles hôtes sont automatiquement créés pour l’ensemble des plages nommées, les objets de liste et les graphiques dans le classeur. Vous pouvez modifier le nom de la <xref:Microsoft.Office.Tools.Excel.Chart> contrôle à l’aide de la **propriétés** fenêtre.  
  
#### <a name="to-change-the-name-of-the-chart-control"></a>Pour modifier le nom du contrôle Chart  
  
1.  Sélectionnez le <xref:Microsoft.Office.Tools.Excel.Chart> contrôler dans le concepteur et modifiez les propriétés suivantes dans le **propriétés** fenêtre.  
  
    |Propriété|Valeur|  
    |--------------|-----------|  
    |**Nom**|**dataChart**|  
    |**HasLegend**|**false**|  
  
## <a name="adding-controls"></a>Ajout de contrôles  
 Cette feuille de calcul utilise des cases d’option pour permettre aux utilisateurs de modifier rapidement le style de graphique. Toutefois, les cases d’option doivent être exclusifs : lorsqu’un bouton est sélectionné, aucun autre bouton dans le groupe ne peut être sélectionné en même temps. Ce comportement ne se produit pas par défaut lorsque vous ajoutez plusieurs boutons de case d’option à une feuille de calcul.  
  
 Permet d’ajouter ce problème consiste à regrouper les cases d’option sur un contrôle utilisateur, écrire votre code derrière le contrôle utilisateur, puis ajoutez le contrôle utilisateur à la feuille de calcul.  
  
#### <a name="to-add-a-user-control"></a>Pour ajouter un contrôle utilisateur  
  
1.  Sélectionnez le **mon graphique Excel** projet **l’Explorateur de solutions**.  
  
2.  Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.  
  
3.  Dans le **ajouter un nouvel élément** boîte de dialogue, cliquez sur **contrôle utilisateur**, nommez le contrôle **ChartOptions** et cliquez sur **ajouter**.  
  
#### <a name="to-add-radio-buttons-to-the-user-control"></a>Pour ajouter des cases d’option au contrôle utilisateur  
  
1.  Si le contrôle utilisateur n’est pas visible dans le concepteur, double-cliquez sur **ChartOptions** dans **l’Explorateur de solutions**.  
  
2.  À partir de la **contrôles communs** onglet de la **boîte à outils**, faites glisser un **case** contrôler au contrôle utilisateur et modifiez les propriétés suivantes.  
  
    |Propriété|Valeur|  
    |--------------|-----------|  
    |**Nom**|**columnChart**|  
    |**Text**|**Histogramme**|  
  
3.  Ajouter un deuxième bouton radio au contrôle utilisateur et modifiez les propriétés suivantes.  
  
    |Propriété|Valeur|  
    |--------------|-----------|  
    |**Nom**|**barChart**|  
    |**Text**|**Graphique à barres**|  
  
4.  Ajoutez une troisième case vers le contrôle utilisateur et modifiez les propriétés suivantes.  
  
    |Propriété|Valeur|  
    |--------------|-----------|  
    |**Nom**|**lineChart**|  
    |**Text**|**Graphique en courbes**|  
  
5.  Ajoutez une quatrième case d’option au contrôle utilisateur et modifiez les propriétés suivantes.  
  
    |Propriété|Valeur|  
    |--------------|-----------|  
    |**Nom**|**areaBlockChart**|  
    |**Text**|**Graphique en secteurs**|  
  
 Ensuite, écrivez le code pour mettre à jour le graphique lorsque vous cliquez sur une case d’option.  
  
## <a name="changing-the-chart-style-when-a-radio-button-is-selected"></a>Modifier le graphique Style lorsqu’un bouton Radio est sélectionné.  
 Vous pouvez maintenant ajouter le code pour modifier le style de graphique. Pour ce faire, créez un événement public sur le contrôle utilisateur, ajoutez une propriété pour définir le type de sélection et créer un gestionnaire d’événements pour le `CheckedChanged` événement de chacune des cases.  
  
#### <a name="to-create-an-event-and-property-on-a-user-control"></a>Pour créer un événement et une propriété sur un contrôle utilisateur  
  
1.  Dans **l’Explorateur de solutions**, cliquez sur le contrôle utilisateur, puis cliquez sur **afficher le Code**.  
  
2.  Ajoutez du code pour le `ChartOptions` classe pour créer un `SelectionChanged` événement et le `Selection` propriété.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#13)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#13)]  
  
#### <a name="to-handle-the-checkedchanged-event-of-the-radio-buttons"></a>Pour gérer l’événement CheckedChanged des boutons radio  
  
1.  Définissez le type de graphique dans le gestionnaire d’événements `CheckedChanged` de la case d'option `areaBlockChart`, puis déclenchez l'événement.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#14)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#14)]  
  
2.  Définissez le type de graphique dans le gestionnaire d’événements `CheckedChanged` de la case d'option `barChart`.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#15)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#15)]  
  
3.  Définissez le type de graphique dans le gestionnaire d’événements `CheckedChanged` de la case d'option `columnChart`.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#16)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#16)]  
  
4.  Définissez le type de graphique dans le gestionnaire d’événements `CheckedChanged` de la case d'option `lineChart`.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#17)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#17)]  
  
5.  En C#, vous devez ajouter des gestionnaires d'événements pour les cases d'option. Vous pouvez ajouter du code au constructeur `ChartOptions`, sous l'appel à `InitializeComponent`. Pour plus d’informations sur la création de gestionnaires d’événements, consultez [Comment : créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#18)]  
  
## <a name="adding-the-user-control-to-the-worksheet"></a>Ajout du contrôle utilisateur à la feuille de calcul  
 Lorsque vous générez la solution, le nouveau contrôle utilisateur est automatiquement ajouté à la **boîte à outils**. Vous pouvez ensuite faire glisser le contrôle à partir de la **boîte à outils** à votre feuille de calcul.  
  
#### <a name="to-add-the-user-control-your-worksheet"></a>Pour ajouter le contrôle utilisateur à votre feuille de calcul  
  
1.  Dans le menu **Générer** , cliquez sur **Générer la solution**.  
  
     Le **ChartOptions** contrôle utilisateur est ajouté à la **boîte à outils**.  
  
2.  Dans **l’Explorateur de solutions**, avec le bouton droit **Sheet1.vb** ou **Sheet1.cs**, puis cliquez sur **Concepteur de vue**.  
  
3.  Faites glisser le **ChartOptions** contrôle depuis la **boîte à outils** à la feuille de calcul.  
  
     Un nouveau contrôle nommé `my_Excel_Chart_ChartOptions1` est ajouté à votre projet.  
  
4.  Modifier le nom du contrôle à **ChartOptions1**.  
  
## <a name="changing-the-chart-type"></a>Changement de type de graphique  
 Pour modifier le type de graphique, créez un gestionnaire d’événements qui définit le style en fonction de l’option sélectionnée dans le contrôle utilisateur.  
  
#### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-worksheet"></a>Pour modifier le type de graphique qui est affiché dans la feuille de calcul  
  
1.  Ajoutez le gestionnaire d'événements suivant à la classe `Sheet1`.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#19)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#19)]  
  
2.  En c#, vous devez ajouter un gestionnaire d’événements pour le contrôle utilisateur à la <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> événement tel qu’indiqué ci-dessous. Pour plus d’informations sur la création de gestionnaires d’événements, consultez [Comment : créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#20)]  
  
## <a name="testing-the-application"></a>Test de l'application  
 Vous pouvez maintenant tester votre classeur pour vérifier que le style du graphique est correct lorsque vous sélectionnez une case d’option.  
  
#### <a name="to-test-your-workbook"></a>Pour tester votre classeur  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Sélectionnez plusieurs cases d'option.  
  
3.  Confirmez que le style de graphique change pour refléter la sélection.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Cette procédure pas à pas présente les notions de base de l’utilisation de cases d’option et des styles de graphique dans les feuilles de calcul. Voici quelques tâches susceptibles de venir après :  
  
-   Déploiement du projet. Pour plus d’informations, consultez [déploiement d’une Solution Office](../vsto/deploying-an-office-solution.md).  
  
-   Utilisation d'un bouton pour renseigner une zone de texte. Pour plus d’informations, consultez [procédure pas à pas : affichage de texte dans une zone de texte dans une feuille de calcul à l’aide d’un bouton](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).  
  
-   Modifier la mise en forme dans une feuille de calcul à l’aide de cases à cocher. Pour plus d’informations, consultez [procédure pas à pas : modification de feuille de calcul mise en forme à l’aide de contrôles CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures pas à pas utilisant Excel](../vsto/walkthroughs-using-excel.md)  
  
  