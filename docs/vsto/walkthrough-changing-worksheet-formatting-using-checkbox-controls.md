---
title: 'Procédure pas à pas : Modifier la mise en forme de feuille de calcul à l’aide de contrôles CheckBox'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, changing formatting using managed controls
- worksheets, check box controls
- controls [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: adc12d920fd3dc128bf23f92508fef8d239b4e8d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53935097"
---
# <a name="walkthrough-change-worksheet-formatting-using-checkbox-controls"></a>Procédure pas à pas : Modifier la mise en forme de feuille de calcul à l’aide de contrôles CheckBox
  Cette procédure pas à pas montre les principes fondamentaux de l’utilisation de cases à cocher sur une feuille de calcul Microsoft Office Excel pour modifier la mise en forme. Vous allez utiliser les outils de développement Office dans Visual Studio pour créer et ajouter du code à votre projet. Pour voir le résultat dans un exemple complet, consultez l’exemple des contrôles Excel [exemples de développement Office et des procédures pas à pas](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Pendant cette procédure pas à pas, vous allez apprendre à :  
  
-   Ajouter du texte et des contrôles à une feuille de calcul.  
  
-   Mettre en forme le texte lorsqu’une option est sélectionnée.  
  
-   Votre projet de test.  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l’interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L’édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="create-the-project"></a>Créer le projet  
 Dans cette étape, vous allez créer un projet de classeur Excel à l’aide de Visual Studio.  
  
### <a name="to-create-a-new-project"></a>Pour créer un projet  
  
1.  Créer un projet de classeur Excel portant le nom **mise en forme Excel de mes**. Assurez-vous que l’option **créer un nouveau document** est sélectionné. Pour plus d'informations, voir [Procédure : Créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio ouvre le nouveau classeur Excel dans le concepteur et ajoute le **mise en forme Excel de mes** projet **l’Explorateur de solutions**.  
  
## <a name="add-text-and-controls-to-the-worksheet"></a>Ajouter du texte et des contrôles à la feuille de calcul  
 Pour cette procédure pas à pas, vous aurez besoin de trois <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> contrôles et du texte dans un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle.  
  
### <a name="to-add-three-check-boxes"></a>Pour ajouter les trois cases à cocher  
  
1.  Vérifiez que le classeur est ouvert dans le concepteur Visual Studio et que `Sheet1` est ouvert.  
  
2.  À partir de la **contrôles communs** onglet de la **boîte à outils**, faites glisser un <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> contrôle vers ou à côté de la cellule **B2** dans **Sheet1**.  
  
3.  À partir de la **vue** menu, sélectionnez **propriétés** fenêtre.  
  
4.  Veillez à ce que **Checkbox1** est visible dans la zone de liste objet nom de le **propriétés** fenêtre et modifiez les propriétés suivantes :  
  
    |Propriété|Value|  
    |--------------|-----------|  
    |**Name**|**applyBoldFont**|  
    |**Text**|**Gras**|  
  
5.  Faites glisser une deuxième case à cocher sur ou près cellule **B4** et modifiez les propriétés suivantes :  
  
    |Propriété|Value|  
    |--------------|-----------|  
    |**Name**|**applyItalicFont**|  
    |**Text**|**Italique**|  
  
6.  Faites glisser une troisième case à cocher sur ou près cellule **B6** et modifiez les propriétés suivantes :  
  
    |Propriété|Value|  
    |--------------|-----------|  
    |**Name**|**applyUnderlineFont**|  
    |**Text**|**Trait de soulignement**|  
  
7.  Sélectionnez tous les contrôles de case à cocher trois tout en maintenant la **Ctrl** clé.  
  
8.  Dans le groupe de la disposition de l’onglet Format dans Excel, cliquez sur **Align**, puis cliquez sur **Aligner à gauche**.  
  
     Les contrôles de case à cocher trois sont alignés sur le côté gauche, à la position du premier contrôle que vous avez sélectionné.  
  
     Ensuite, vous faites glisser un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle à la feuille de calcul.  
  
    > [!NOTE]  
    >  Vous pouvez également ajouter le <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle en tapant **textFont** dans le **nom** boîte.  
  
#### <a name="to-add-text-to-a-namedrange-control"></a>Pour ajouter du texte à un contrôle NamedRange  
  
1. À partir de la **contrôles Excel** onglet de la boîte à outils, faites glisser un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle de cellule **B9**.  
  
2. Vérifiez que **$B$ 9** apparaît dans la zone de texte modifiable et que la cellule **B9** est sélectionné. Si elle n’est pas le cas, cliquez sur cellule **B9** pour le sélectionner.  
  
3. Cliquez sur **OK**.  
  
4. Cellule **B9** devient une plage nommée `NamedRange1`.  
  
    Il n’existe aucune indication visible sur la feuille de calcul, mais `NamedRange1` s’affiche dans le **zoneNom** (juste au-dessus de la feuille de calcul sur le côté gauche) quand la cellule **B9** est sélectionné.  
  
5. Veillez à ce que **NamedRange1** est visible dans la zone de liste objet nom de le **propriétés** fenêtre et modifiez les propriétés suivantes :  
  
   |Propriété|Value|  
   |--------------|-----------|  
   |**Name**|**textFont**|  
   |**Value2**|**Cliquez sur une case à cocher pour modifier la mise en forme du texte.**|  
  
   Ensuite, écrivez le code pour mettre en forme le texte lorsqu’une option est sélectionnée.  
  
## <a name="format-the-text-when-an-option-is-selected"></a>Mettre en forme le texte lorsqu’une option est sélectionnée.  
 Dans cette section, vous allez écrire le code afin que lorsque l’utilisateur sélectionne une option de mise en forme, le format du texte dans la feuille de calcul est modifié.  
  
### <a name="to-change-formatting-when-a-check-box-is-selected"></a>Pour modifier la mise en forme lors d’une case à cocher est sélectionnée.  
  
1.  Avec le bouton droit **Sheet1**, puis cliquez sur **afficher le Code** dans le menu contextuel.  
  
2.  Ajoutez le code suivant à la <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements de la `applyBoldFont` case à cocher :  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#7)]  
  
3.  Ajoutez le code suivant à la <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements de la `applyItalicFont` case à cocher :  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#8)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#8)]  
  
4.  Ajoutez le code suivant à la <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements de la `applyUnderlineFont` case à cocher :  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#9)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#9)]  
  
5.  En c#, vous devez ajouter des gestionnaires d’événements pour les cases à cocher pour le <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> événement comme indiqué ci-dessous. Pour plus d’informations sur la création de gestionnaires d’événements, consultez [Comment : Créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#10)]  
  
## <a name="test-the-application"></a>Tester l’application  
 Vous pouvez maintenant tester votre classeur pour vous assurer que le texte est mis en forme correctement lorsque vous activez ou désactivez une case à cocher.  
  
### <a name="to-test-your-workbook"></a>Pour tester votre classeur  
  
1.  Appuyez sur **F5** pour exécuter votre projet.  
  
2.  Activez ou désactivez une case à cocher.  
  
3.  Vérifiez que le texte est mis en forme correctement.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Cette procédure pas à pas montre les principes fondamentaux d’à l’aide des cases à cocher et la mise en forme de texte sur des feuilles de calcul Excel. Voici quelques tâches susceptibles de venir après :  
  
-   Déploiement du projet. Pour plus d’informations, consultez [déployer une solution Office à l’aide de ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
-   Utilisation d'un bouton pour renseigner une zone de texte. Pour plus d’informations, consultez [Procédure pas à pas : Afficher du texte dans une zone de texte dans une feuille de calcul à l’aide d’un bouton](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures pas à pas utilisant Excel](../vsto/walkthroughs-using-excel.md)   
 [NamedRange (contrôle)](../vsto/namedrange-control.md)   
 [Limitations des contrôles Windows Forms sur des documents Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
