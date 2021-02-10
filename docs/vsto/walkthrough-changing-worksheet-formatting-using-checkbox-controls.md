---
title: Modifier la mise en forme d’une feuille de calcul à l’aide de contrôles CheckBox
description: Découvrez comment vous pouvez utiliser les outils de développement Office dans Visual Studio pour créer et ajouter du code à votre projet.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, changing formatting using managed controls
- worksheets, check box controls
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 908660693abce2f2adf07d98e7f2a451a8f3c8e5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956592"
---
# <a name="walkthrough-change-worksheet-formatting-using-checkbox-controls"></a>Procédure pas à pas : modifier la mise en forme d’une feuille de calcul à l’aide
  Cette procédure pas à pas montre les principes de base de l’utilisation de cases à cocher dans une feuille de calcul Excel Microsoft Office pour modifier la mise en forme. Vous allez utiliser les outils de développement Office dans Visual Studio pour créer et ajouter du code à votre projet. Pour afficher le résultat sous forme d’exemple terminé, consultez l’exemple contrôles Excel dans les [exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md).

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Pendant cette procédure pas à pas, vous allez apprendre à :

- Ajoutez du texte et des contrôles à une feuille de calcul.

- Mettre en forme le texte lorsqu’une option est sélectionnée.

- Testez votre projet.

> [!NOTE]
> Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Créer le projet
 Dans cette étape, vous allez créer un projet de classeur Excel à l’aide de Visual Studio.

### <a name="to-create-a-new-project"></a>Pour créer un projet

1. Créez un projet de classeur Excel avec le nom **mon mise en forme Excel**. Assurez-vous que l’option **créer un nouveau document** est sélectionnée. Pour plus d’informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio ouvre le nouveau classeur Excel dans le concepteur et ajoute le projet de **mise en forme My Excel** à **Explorateur de solutions**.

## <a name="add-text-and-controls-to-the-worksheet"></a>Ajouter du texte et des contrôles à la feuille de calcul
 Pour cette procédure pas à pas, vous aurez besoin de trois <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> contrôles et de texte dans un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle.

### <a name="to-add-three-check-boxes"></a>Pour ajouter trois cases à cocher

1. Vérifiez que le classeur est ouvert dans le concepteur Visual Studio et qu’il `Sheet1` est ouvert.

2. Dans l’onglet **contrôles communs** de la **boîte à outils**, faites glisser un <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> contrôle vers ou à côté de la cellule **B2** dans **Feuil1**.

3. Dans le menu **affichage** , sélectionnez fenêtre **Propriétés** .

4. Assurez-vous que **CheckBox1** est visible dans la zone de liste nom de l’objet de la fenêtre **Propriétés** , puis modifiez les propriétés suivantes :

    |Propriété|Valeur|
    |--------------|-----------|
    |**Nom**|**applyBoldFont**|
    |**Text**|**Gras**|

5. Faites glisser une deuxième case à cocher sur ou à proximité de la cellule **B4** et modifiez les propriétés suivantes :

    |Propriété|Valeur|
    |--------------|-----------|
    |**Nom**|**applyItalicFont**|
    |**Text**|**Italique**|

6. Faites glisser une troisième case à cocher sur ou à proximité de la cellule **B6** et modifiez les propriétés suivantes :

    |Propriété|Valeur|
    |--------------|-----------|
    |**Nom**|**applyUnderlineFont**|
    |**Text**|**Souligner**|

7. Sélectionnez les trois contrôles de case à cocher en maintenant la touche **CTRL** enfoncée.

8. Dans le groupe organiser de l’onglet Format dans Excel, cliquez sur **Aligner**, puis sur **Aligner à gauche**.

     Les trois contrôles de case à cocher sont alignés sur le côté gauche, à la position du premier contrôle que vous avez sélectionné.

     Ensuite, vous allez faire glisser un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle vers la feuille de calcul.

    > [!NOTE]
    > Vous pouvez également ajouter le <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle en tapant **textFont** dans la zone **nom** .

#### <a name="to-add-text-to-a-namedrange-control"></a>Pour ajouter du texte à un contrôle NamedRange

1. À partir de l’onglet **contrôles Excel** de la boîte à outils, faites glisser un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle vers la cellule **B9**.

2. Vérifiez que **$B $9** apparaît dans la zone de texte modifiable et que la cellule **B9** est sélectionnée. Si ce n’est pas le cas, cliquez sur la cellule **B9** pour la sélectionner.

3. Cliquez sur **OK**.

4. La cellule **B9** devient une plage nommée `NamedRange1` .

    Il n’existe aucune indication visible sur la feuille de calcul, mais elle `NamedRange1` apparaît dans la **zone Nom** (juste au-dessus de la feuille de calcul sur le côté gauche) lorsque la cellule **B9** est sélectionnée.

5. Assurez-vous que la propriété **NamedRange1** est visible dans la zone de liste nom de l’objet de la fenêtre **Propriétés** , puis modifiez les propriétés suivantes :

   |Propriété|Valeur|
   |--------------|-----------|
   |**Nom**|**textFont**|
   |**Value2**|**Cliquez sur une case à cocher pour modifier la mise en forme de ce texte.**|

   Ensuite, écrivez le code pour mettre en forme le texte lorsqu’une option est sélectionnée.

## <a name="format-the-text-when-an-option-is-selected"></a>Mettre en forme le texte quand une option est sélectionnée
 Dans cette section, vous allez écrire du code afin que lorsque l’utilisateur sélectionne une option de mise en forme, le format du texte dans la feuille de calcul est modifié.

### <a name="to-change-formatting-when-a-check-box-is-selected"></a>Pour modifier la mise en forme lorsqu’une case à cocher est activée

1. Cliquez avec le bouton droit sur **Feuil1**, puis cliquez sur **afficher le code** dans le menu contextuel.

2. Ajoutez le code suivant au <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements de la case `applyBoldFont` à cocher :

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#7)]

3. Ajoutez le code suivant au <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements de la case `applyItalicFont` à cocher :

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#8)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#8)]

4. Ajoutez le code suivant au <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements de la case `applyUnderlineFont` à cocher :

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#9)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#9)]

5. En C#, vous devez ajouter des gestionnaires d’événements pour les cases à cocher à l' <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> événement, comme indiqué ci-dessous. Pour plus d’informations sur la création de gestionnaires d’événements, consultez [Comment : créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#10)]

## <a name="test-the-application"></a>Tester l’application
 Vous pouvez maintenant tester votre classeur pour vous assurer que le texte est mis en forme correctement lorsque vous activez ou désactivez une case à cocher.

### <a name="to-test-your-workbook"></a>Pour tester votre classeur

1. Appuyez sur **F5** pour exécuter votre projet.

2. Activer ou désactiver une case à cocher.

3. Confirmez que le texte est correctement mis en forme.

## <a name="next-steps"></a>Étapes suivantes
 Cette procédure pas à pas montre les bases de l’utilisation des cases à cocher et de la mise en forme du texte dans les feuilles de calcul Excel. Voici quelques tâches susceptibles de venir après :

- Déploiement du projet. Pour plus d’informations, consultez [déployer une solution Office à l’aide de ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).
- Utilisation d'un bouton pour renseigner une zone de texte. Pour plus d’informations, consultez [procédure pas à pas : affichage de texte dans une zone de texte d’une feuille de calcul à l’aide d’un bouton](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).

## <a name="see-also"></a>Voir aussi
- [Procédures pas à pas utilisant Excel](../vsto/walkthroughs-using-excel.md)
- [NamedRange, contrôle](../vsto/namedrange-control.md)
- [Limitations des contrôles de Windows Forms sur les documents Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
