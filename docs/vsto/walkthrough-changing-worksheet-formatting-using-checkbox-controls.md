---
title: "Procédure pas à pas : Modification de mise en forme de feuille de calcul à l’aide de contrôles de case à cocher | Documents Microsoft"
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
- worksheets, changing formatting using managed controls
- worksheets, check box controls
- controls [Office development in Visual Studio], adding to worksheets
ms.assetid: 4be79613-50a0-428e-9816-aadbc098272a
caps.latest.revision: "70"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7f10b0ed77dc9d5f97b6fc2fc4f218c86dafee41
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-changing-worksheet-formatting-using-checkbox-controls"></a>Procédure pas à pas : modification de la mise en forme d'une feuille de calcul à l'aide de contrôles CheckBox
  Cette procédure pas à pas présente les notions de base de l’utilisation de cases à cocher dans une feuille de calcul Microsoft Office Excel pour modifier la mise en forme. Vous utiliserez des outils de développement Office dans Visual Studio pour créer et ajouter du code à votre projet. Pour afficher le résultat sous la forme d’un exemple complet, consultez l’exemple des contrôles Excel [exemples de développement Office et des procédures pas à pas](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Pendant cette procédure pas à pas, vous allez apprendre à :  
  
-   Ajouter du texte et des contrôles à une feuille de calcul.  
  
-   Mettre en forme le texte lorsqu’une option est sélectionnée.  
  
-   Votre projet de test.  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Création du projet  
 Dans cette étape, vous allez créer un projet de classeur Excel à l’aide de Visual Studio.  
  
#### <a name="to-create-a-new-project"></a>Pour créer un projet  
  
1.  Créer un projet de classeur Excel portant le nom **My Excel Formatting**. Assurez-vous que **créer un nouveau document** est sélectionnée. Pour plus d'informations, consultez [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio ouvre le nouveau classeur Excel dans le concepteur et ajoute le **My Excel Formatting** projet **l’Explorateur de solutions**.  
  
## <a name="adding-text-and-controls-to-the-worksheet"></a>Ajout de texte et des contrôles à la feuille de calcul  
 Pour cette procédure pas à pas, vous aurez besoin de trois <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> contrôles et du texte dans un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle.  
  
#### <a name="to-add-three-check-boxes"></a>Pour ajouter trois cases à cocher  
  
1.  Vérifiez que le classeur est ouvert dans le concepteur Visual Studio et que `Sheet1` est ouvert.  
  
2.  À partir de la **contrôles communs** onglet de la **boîte à outils**, faites glisser un <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> contrôle à ou près de cellule **B2** dans **Feuil1**.  
  
3.  À partir de la **vue** menu, sélectionnez **propriétés** fenêtre.  
  
4.  Assurez-vous que **Checkbox1** est visible dans la zone de liste objet nom de le **propriétés** fenêtre et modifiez les propriétés suivantes :  
  
    |Propriété|Valeur|  
    |--------------|-----------|  
    |**Nom**|**applyBoldFont**|  
    |**Text**|**Gras**|  
  
5.  Faites glisser une deuxième case à cocher sur ou à côté de la cellule **B4** et modifiez les propriétés suivantes :  
  
    |Propriété|Valeur|  
    |--------------|-----------|  
    |**Nom**|**applyItalicFont**|  
    |**Text**|**Italique**|  
  
6.  Faites glisser une troisième case à cocher sur ou à côté de la cellule **B6** et modifiez les propriétés suivantes :  
  
    |Propriété|Valeur|  
    |--------------|-----------|  
    |**Nom**|**applyUnderlineFont**|  
    |**Text**|**Soulignement**|  
  
7.  Sélectionnez tous les contrôles de case à cocher trois tout en maintenant la touche CTRL ENFONCÉE.  
  
8.  Dans le groupe de la disposition de l’onglet Format dans Excel, cliquez sur **Align**, puis cliquez sur **Aligner à gauche**.  
  
     Les contrôles de case à cocher trois sont alignés à gauche, à la position du premier contrôle que vous avez sélectionné.  
  
     Ensuite, vous faites glisser un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle à la feuille de calcul.  
  
    > [!NOTE]  
    >  Vous pouvez également ajouter le <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle en tapant **textFont** dans les **nom** boîte.  
  
#### <a name="to-add-text-to-a-namedrange-control"></a>Pour ajouter du texte à un contrôle NamedRange  
  
1.  À partir de la **contrôles Excel** onglet de la boîte à outils, faites glisser un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle cellule **B9**.  
  
2.  Vérifiez que **$B$ 9** s’affiche dans la zone de texte modifiable et que la cellule **B9** est sélectionnée. Si elle n’est pas le cas, cliquez sur cellule **B9** pour le sélectionner.  
  
3.  Cliquez sur **OK**.  
  
4.  Cellule **B9** devient une plage nommée `NamedRange1`.  
  
     Il n’existe aucune indication visible sur la feuille de calcul, mais `NamedRange1` s’affiche dans le **zone nom** (juste au-dessus de la feuille de calcul sur le côté gauche) lorsque la cellule **B9** est sélectionnée.  
  
5.  Assurez-vous que **NamedRange1** est visible dans la zone de liste objet nom de le **propriétés** fenêtre et modifiez les propriétés suivantes :  
  
    |Propriété|Valeur|  
    |--------------|-----------|  
    |**Nom**|**textFont**|  
    |**Valeur2**|**Cliquez sur une case à cocher pour modifier la mise en forme du texte.**|  
  
 Ensuite, écrivez le code pour mettre en forme le texte lorsqu’une option est sélectionnée.  
  
## <a name="formatting-the-text-when-an-option-is-selected"></a>Mise en forme le texte lorsqu’une Option est sélectionnée.  
 Dans cette section, vous allez écrire le code afin que lorsque l’utilisateur sélectionne une option de mise en forme, le format du texte dans la feuille de calcul est modifié.  
  
#### <a name="to-change-formatting-when-a-check-box-is-selected"></a>Pour modifier la mise en forme lors d’une case à cocher est activée.  
  
1.  Avec le bouton droit **Feuil1**, puis cliquez sur **afficher le Code** dans le menu contextuel.  
  
2.  Ajoutez le code suivant à la <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements de le `applyBoldFont` case à cocher :  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#7)]  
  
3.  Ajoutez le code suivant à la <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements de le `applyItalicFont` case à cocher :  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#8)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#8)]  
  
4.  Ajoutez le code suivant à la <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements de le `applyUnderlineFont` case à cocher :  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#9)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#9)]  
  
5.  En c#, vous devez ajouter des gestionnaires d’événements pour les cases à cocher pour le <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> événement tel qu’indiqué ci-dessous. Pour plus d’informations sur la création de gestionnaires d’événements, consultez [Comment : créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#10)]  
  
## <a name="testing-the-application"></a>Test de l'application  
 Vous pouvez maintenant tester votre classeur pour vous assurer que le texte est mis en forme correctement lorsque vous activez ou désactivez une case à cocher.  
  
#### <a name="to-test-your-workbook"></a>Pour tester votre classeur  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Activez ou désactivez une case à cocher.  
  
3.  Vérifiez que le texte est mis en forme correctement.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Cette procédure pas à pas illustre les principes fondamentaux de l’utilisation de cases à cocher et mise en forme du texte dans des feuilles de calcul Excel. Voici quelques tâches susceptibles de venir après :  
  
-   Déploiement du projet. Pour plus d’informations, consultez [déploiement d’une Solution Office à l’aide de ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
-   Utilisation d'un bouton pour renseigner une zone de texte. Pour plus d’informations, consultez [procédure pas à pas : affichage de texte dans une zone de texte dans une feuille de calcul à l’aide d’un bouton](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures pas à pas utilisant Excel](../vsto/walkthroughs-using-excel.md)   
 [NamedRange (contrôle)](../vsto/namedrange-control.md)   
 [Limitations des contrôles Windows Forms dans les documents Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  