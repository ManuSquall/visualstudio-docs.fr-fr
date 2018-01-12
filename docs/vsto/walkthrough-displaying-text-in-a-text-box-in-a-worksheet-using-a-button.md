---
title: "Procédure pas à pas : Affichage de texte dans une zone de texte dans une feuille de calcul à l’aide d’un bouton | Documents Microsoft"
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
- text [Office development in Visual Studio], displaying worksheets
- worksheets, displaying text
- text boxes, displaying text in worksheets
- text [Office development in Visual Studio], text boxes
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7b88940aa1329bc330e5d8bb7d114c21fac3dacb
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button"></a>Procédure pas à pas : affichage de texte dans une zone de texte d'une feuille de calcul à l'aide d'un bouton
  Cette procédure pas à pas présente les notions de base de l’utilisation des boutons et des zones de texte dans des feuilles de calcul Microsoft Office Excel et comment créer des projets Excel à l’aide des outils de développement Office dans Visual Studio. Pour afficher le résultat sous la forme d’un exemple complet, consultez l’exemple des contrôles Excel [exemples de développement Office et des procédures pas à pas](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Pendant cette procédure pas à pas, vous allez apprendre à :  
  
-   Ajouter des contrôles à une feuille de calcul.  
  
-   Remplir une zone de texte lorsqu’un clic est effectué.  
  
-   Votre projet de test.  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l’interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L’édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Création du projet  
 Dans cette étape, vous allez créer un projet de classeur Excel à l’aide de Visual Studio.  
  
#### <a name="to-create-a-new-project"></a>Pour créer un projet  
  
1.  Créer un projet de classeur Excel portant le nom **mon bouton Excel**. Assurez-vous que **créer un nouveau document** est sélectionnée. Pour plus d'informations, consultez [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio ouvre le nouveau classeur Excel dans le concepteur et ajoute le **mon bouton Excel** projet **l’Explorateur de solutions**.  
  
## <a name="adding-controls-to-the-worksheet"></a>Ajout de contrôles à la feuille de calcul  
 Pour cette procédure pas à pas, vous devez un bouton et une zone de texte sur la première feuille de calcul.  
  
#### <a name="to-add-a-button-and-a-text-box"></a>Pour ajouter un bouton et une zone de texte  
  
1.  Vérifiez que le **mes Excel Button.xlsx** classeur est ouvert dans le concepteur Visual Studio, avec `Sheet1` affiché.  
  
2.  À partir de la **contrôles communs** onglet de la boîte à outils, faites glisser un <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> à `Sheet1`.  
  
3.  À partir de la **vue** menu, sélectionnez **fenêtre Propriétés**.  
  
4.  Assurez-vous que **TextBox1** est visible dans le **propriétés** la liste déroulante de la fenêtre et modifier le **nom** propriétés de la zone de texte **displayText**.  
  
5.  Faites glisser un **bouton** contrôler sur `Sheet1` et modifiez les propriétés suivantes :  
  
    |Propriété|Value|  
    |--------------|-----------|  
    |**Name**|**insertText**|  
    |**Text**|**Insérer du texte**|  
  
 Maintenant écrire le code à exécuter lorsque le bouton est activé.  
  
## <a name="populating-the-text-box-when-the-button-is-clicked"></a>Remplissage de la zone de texte lorsque le bouton est activé.  
 Chaque fois que l’utilisateur clique sur le bouton, **Hello World !** est ajouté à la zone de texte.  
  
#### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Pour écrire dans la zone de texte lorsqu'un clic est effectué  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit **Feuil1**, puis cliquez sur **afficher le Code** dans le menu contextuel.  
  
2.  Ajoutez le code suivant à la <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements du bouton :  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#11)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#11)]  
  
3.  En c#, vous devez ajouter un gestionnaire d’événements pour le <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> événement tel qu’indiqué ci-dessous. Pour plus d’informations sur la création de gestionnaires d’événements, consultez [Comment : créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#12)]  
  
## <a name="testing-the-application"></a>Test de l'application  
 Vous pouvez maintenant tester votre classeur pour vous assurer que le message **Hello World !** s’affiche dans la zone de texte lorsque vous cliquez sur le bouton.  
  
#### <a name="to-test-your-workbook"></a>Pour tester votre classeur  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Cliquez sur le bouton.  
  
3.  Vérifiez que **Hello World !** s’affiche dans la zone de texte.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Cette procédure pas à pas présente les notions de base de l’utilisation des boutons et des zones de texte dans des feuilles de calcul Excel. Voici quelques tâches susceptibles de venir après :  
  
-   Déploiement du projet. Pour plus d’informations, consultez [déploiement d’une Solution Office](../vsto/deploying-an-office-solution.md).  
  
-   À l’aide des cases à cocher pour modifier la mise en forme. Pour plus d’informations, consultez [procédure pas à pas : modification de feuille de calcul mise en forme à l’aide de contrôles CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : ajouter des contrôles Windows Forms à des Documents Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Procédures pas à pas utilisant Excel](../vsto/walkthroughs-using-excel.md)   
 [Limitations des contrôles Windows Forms dans les documents Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  