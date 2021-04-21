---
title: Mettre à jour un graphique dans une feuille de calcul à l’aide de cases
description: Découvrez les principes de base de l’utilisation des cases d’option dans une feuille de calcul Microsoft Excel pour offrir à l’utilisateur un moyen de basculer rapidement entre les options.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, updating using managed controls
- controls [Office development in Visual Studio], updating worksheets
- worksheets, using radio buttons
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3d61579181f00d97a74cc48e022bb5d93a05c0f0
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828174"
---
# <a name="walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons"></a>Procédure pas à pas : mise à jour d'un graphique dans une feuille de calcul à l'aide de cases d'option
  Cette procédure pas à pas montre les principes fondamentaux de l’utilisation des cases d’option dans une feuille de calcul Excel Microsoft Office pour permettre à l’utilisateur de basculer rapidement entre les options. Dans ce cas, les options modifient le style d’un graphique.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Pour afficher le résultat sous forme d’exemple terminé, consultez l’exemple contrôles Excel dans les [exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md).

 Cette procédure pas à pas décrit les tâches suivantes :

- Ajout d’un groupe de cases d’option à une feuille de calcul.

- Changement de style de graphique quand une option est sélectionnée.

> [!NOTE]
> Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="add-a-chart-to-a-worksheet"></a>Ajouter un graphique à une feuille de calcul
 Vous pouvez créer un projet de classeur Excel qui personnalise un classeur existant. Dans cette procédure pas à pas, vous allez ajouter un graphique à un classeur, puis utiliser ce classeur dans une nouvelle solution Excel. La source de données dans cette procédure pas à pas est une feuille de calcul nommée **Data for Chart**.

### <a name="to-add-the-data"></a>Pour ajouter les données

1. Ouvrez Microsoft Excel.

2. Cliquez avec le bouton droit sur l’onglet **Sheet3** , puis cliquez sur **Renommer** dans le menu contextuel.

3. Renommez la feuille en **données pour Chart**.

4. Ajoutez les données suivantes aux **données pour le graphique** dont la cellule a4 est l’angle supérieur gauche et le coin inférieur droit.

   |Région/trimestre|Q1|Q2|Q3|Q4|
   |-|--------|--------|--------|--------|
   |West|500|550|550|600|
   |Est|600|625|675|700|
   |Nord|450|470|490|510|
   |Sud|800|750|775|790|

   Ensuite, ajoutez un graphique à la première feuille de calcul pour afficher les données.

### <a name="to-add-a-chart-in-excel"></a>Pour ajouter un graphique dans Excel

1. Sous l’onglet **Insérer** , dans le groupe **graphiques** , cliquez sur **colonne**, puis sur **tous les types de graphiques**.

2. Dans la boîte de dialogue **Insérer un graphique** , cliquez sur **OK**.

3. Sous l’onglet **conception** , dans le groupe **données** , cliquez sur **Sélectionner des données**.

4. Dans la boîte de dialogue **Sélectionner une source de données** , cliquez dans la zone **plage ChartData** et effacez toutes les sélections par défaut.

5. Dans les **données de** la feuille de graphique, sélectionnez le bloc de cellules qui contient les nombres, ce qui inclut a4 dans le coin supérieur gauche de la cellule E8 dans le coin inférieur droit.

6. Dans la boîte de dialogue **Sélectionner une source de données** , cliquez sur **OK**.

7. Repositionnez le graphique de sorte que le coin supérieur droit s’aligne avec la cellule **E2**.

8. Enregistrez votre fichier sur le lecteur C et nommez-le **ExcelChart.xlsx**.

9. Quittez Excel.

## <a name="create-a-new-project"></a>Créer un projet
 Dans cette étape, vous allez créer un projet de classeur Excel basé sur le classeur **ExcelChart** .

### <a name="to-create-a-new-project"></a>Pour créer un projet

1. Créez un projet de classeur Excel avec le nom **My Excel Chart**. Dans l’Assistant, sélectionnez **copier un document existant**.

     Pour plus d’informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Cliquez sur le bouton **Parcourir** et accédez au classeur que vous avez créé précédemment dans cette procédure pas à pas.

3. Cliquez sur **OK**.

     Visual Studio ouvre le nouveau classeur Excel dans le concepteur et ajoute le projet **mon graphique Excel** à **Explorateur de solutions**.

## <a name="set-properties-of-the-chart"></a>Définir les propriétés du graphique
 Lorsque vous créez un projet de classeur Excel qui utilise un classeur existant, les contrôles hôtes sont créés automatiquement pour toutes les plages nommées, les objets de liste et les graphiques du classeur. Vous pouvez modifier le nom du <xref:Microsoft.Office.Tools.Excel.Chart> contrôle à l’aide de la fenêtre **Propriétés** .

### <a name="to-change-the-name-of-the-chart-control"></a>Pour modifier le nom du contrôle Chart

1. Sélectionnez le <xref:Microsoft.Office.Tools.Excel.Chart> contrôle dans le concepteur et modifiez les propriétés suivantes dans la fenêtre **Propriétés** .

    |Propriété|Valeur|
    |--------------|-----------|
    |**Nom**|**dataChart**|
    |**HasLegend**|**false**|

## <a name="add-controls"></a>Ajouter des contrôles
 Cette feuille de calcul utilise des cases d’option pour permettre aux utilisateurs de modifier rapidement le style du graphique. Toutefois, les cases d’option doivent être exclusives : lorsqu’un bouton est sélectionné, aucun autre bouton du groupe ne peut être sélectionné en même temps. Ce comportement ne se produit pas par défaut lorsque vous ajoutez plusieurs cases d’option à une feuille de calcul.

 Une façon d’ajouter ce comportement consiste à regrouper les cases d’option sur un contrôle utilisateur, à écrire votre code derrière le contrôle utilisateur, puis à ajouter le contrôle utilisateur à la feuille de calcul.

### <a name="to-add-a-user-control"></a>Pour ajouter un contrôle utilisateur

1. Sélectionnez le projet **My Excel Chart** dans **Explorateur de solutions**.

2. Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.

3. Dans la boîte de dialogue **Ajouter un nouvel élément** , cliquez sur **contrôle utilisateur**, nommez le contrôle **ChartOptions,** puis cliquez sur **Ajouter**.

### <a name="to-add-radio-buttons-to-the-user-control"></a>Pour ajouter des cases d’option au contrôle utilisateur

1. Si le contrôle utilisateur n’est pas visible dans le concepteur, double-cliquez sur **ChartOptions** dans **Explorateur de solutions**.

2. Dans l’onglet **contrôles communs** de la **boîte à outils**, faites glisser un contrôle **case d’option** vers le contrôle utilisateur et modifiez les propriétés suivantes.

   | Propriété | Valeur |
   |----------|------------------|
   | **Nom** | **columnChart** |
   | **Text** | **Histogramme** |

3. Ajoutez une deuxième case d’option au contrôle utilisateur et modifiez les propriétés suivantes.

   | Propriété | Valeur |
   |----------|---------------|
   | **Nom** | **barChart** |
   | **Text** | **Graphique à barres** |

4. Ajoutez une troisième case d’option au contrôle utilisateur et modifiez les propriétés suivantes.

   | Propriété | Valeur |
   |----------|----------------|
   | **Nom** | **lineChart** |
   | **Text** | **Graphique en courbes** |

5. Ajoutez une quatrième case d’option au contrôle utilisateur et modifiez les propriétés suivantes.

   |Propriété|Valeur|
   |--------------|-----------|
   |**Nom**|**areaBlockChart**|
   |**Text**|**Graphique en secteurs**|

   Ensuite, écrivez le code pour mettre à jour le graphique lorsque l’utilisateur clique sur une case d’option.

## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>Modifier le style du graphique lorsqu’une case d’option est sélectionnée
 Vous pouvez maintenant ajouter le code pour modifier le style du graphique. Pour ce faire, créez un événement public sur le contrôle utilisateur, ajoutez une propriété pour définir le type de sélection, puis créez un gestionnaire d’événements pour l' `CheckedChanged` événement de chacune des cases d’option.

### <a name="to-create-an-event-and-property-on-a-user-control"></a>Pour créer un événement et une propriété sur un contrôle utilisateur

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le contrôle utilisateur, puis cliquez sur **afficher le code**.

2. Ajoutez du code à la `ChartOptions` classe pour créer un `SelectionChanged` événement et la `Selection` propriété.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb" id="Snippet13":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs" id="Snippet13":::

### <a name="to-handle-the-checkedchanged-event-of-the-radio-buttons"></a>Pour gérer l’événement CheckedChanged des cases d’option

1. Définissez le type de graphique dans le gestionnaire d’événements `CheckedChanged` de la case d'option `areaBlockChart`, puis déclenchez l'événement.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb" id="Snippet14":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs" id="Snippet14":::

2. Définissez le type de graphique dans le gestionnaire d’événements `CheckedChanged` de la case d'option `barChart`.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb" id="Snippet15":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs" id="Snippet15":::

3. Définissez le type de graphique dans le gestionnaire d’événements `CheckedChanged` de la case d'option `columnChart`.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb" id="Snippet16":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs" id="Snippet16":::

4. Définissez le type de graphique dans le gestionnaire d’événements `CheckedChanged` de la case d'option `lineChart`.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb" id="Snippet17":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs" id="Snippet17":::

5. En C#, vous devez ajouter des gestionnaires d'événements pour les cases d'option. Vous pouvez ajouter du code au constructeur `ChartOptions`, sous l'appel à `InitializeComponent`. Pour plus d’informations sur la création de gestionnaires d’événements, consultez [Comment : créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs" id="Snippet18":::

## <a name="add-the-user-control-to-the-worksheet"></a>Ajouter le contrôle utilisateur à la feuille de calcul
 Lorsque vous générez la solution, le nouveau contrôle utilisateur est automatiquement ajouté à la **boîte à outils**. Vous pouvez ensuite faire glisser le contrôle de la **boîte à outils** vers votre feuille de calcul.

### <a name="to-add-the-user-control-your-worksheet"></a>Pour ajouter le contrôle utilisateur à votre feuille de calcul

1. Dans le menu **Générer**, cliquez sur **Générer la solution**.

     Le contrôle utilisateur **ChartOptions** est ajouté à la **boîte à outils**.

2. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **Feuil1. vb** ou **Feuille1. cs**, puis cliquez sur **Concepteur de vues**.

3. Faites glisser le contrôle **ChartOptions** de la **boîte à outils** vers la feuille de calcul.

     Un nouveau contrôle nommé `my_Excel_Chart_ChartOptions1` est ajouté à votre projet.

4. Remplacez le nom du contrôle par **ChartOptions1**.

## <a name="change-the-chart-type"></a>Modifier le type de graphique
 Pour modifier le type de graphique, créez un gestionnaire d’événements qui définit le style en fonction de l’option sélectionnée dans le contrôle utilisateur.

### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-worksheet"></a>Pour modifier le type de graphique affiché dans la feuille de calcul

1. Ajoutez le gestionnaire d'événements suivant à la classe `Sheet1`.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet19":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet19":::

2. En C#, vous devez ajouter un gestionnaire d’événements pour le contrôle utilisateur à l' <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> événement, comme indiqué ci-dessous. Pour plus d’informations sur la création de gestionnaires d’événements, consultez [Comment : créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet20":::

## <a name="test-the-application"></a>Tester l’application
 Vous pouvez maintenant tester votre classeur pour vérifier que le style du graphique est correct quand vous sélectionnez une case d’option.

### <a name="to-test-your-workbook"></a>Pour tester votre classeur

1. Appuyez sur **F5** pour exécuter votre projet.

2. Sélectionnez plusieurs cases d'option.

3. Confirmez que le style de graphique change pour refléter la sélection.

## <a name="next-steps"></a>Étapes suivantes
 Cette procédure pas à pas montre les concepts de base de l’utilisation des cases d’option et des styles de graphique dans les feuilles de calcul. Voici quelques tâches susceptibles de venir après :

- Déploiement du projet. Pour plus d’informations, consultez [déployer une solution Office](../vsto/deploying-an-office-solution.md).

- Utilisation d'un bouton pour renseigner une zone de texte. Pour plus d’informations, consultez [procédure pas à pas : affichage de texte dans une zone de texte d’une feuille de calcul à l’aide d’un bouton](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).

- Modifiez la mise en forme d’une feuille de calcul à l’aide de cases à cocher. Pour plus d’informations, consultez [procédure pas à pas : modifier la mise en forme des feuilles de calcul à l’aide de contrôles CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>Voir aussi
- [Procédures pas à pas utilisant Excel](../vsto/walkthroughs-using-excel.md)
