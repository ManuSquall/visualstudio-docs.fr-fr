---
title: Afficher le texte dans la zone de texte de la feuille de calcul à l’aide du bouton
description: Découvrez les principes de base de l’utilisation des boutons et des zones de texte dans les feuilles de calcul Microsoft Excel. Créez également des projets Excel à l’aide des outils de développement Office dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], displaying worksheets
- worksheets, displaying text
- text boxes, displaying text in worksheets
- text [Office development in Visual Studio], text boxes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c499800efa783ce252dbf925f307bc64e814420f
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97522641"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-worksheet-using-a-button"></a>Procédure pas à pas : affichage de texte dans une zone de texte d’une feuille de calcul à l’aide d’un bouton
  Cette procédure pas à pas montre les concepts de base de l’utilisation de boutons et de zones de texte sur Microsoft Office des feuilles de calcul Excel, et comment créer des projets Excel à l’aide des outils de développement Office dans Visual Studio. Pour afficher le résultat sous forme d’exemple terminé, consultez l’exemple contrôles Excel dans les [exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md).

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Pendant cette procédure pas à pas, vous allez apprendre à :

- Ajoutez des contrôles à une feuille de calcul.

- Remplir une zone de texte en cas de clic sur un bouton.

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

1. Créez un projet de classeur Excel avec le **bouton nom My Excel**. Assurez-vous que l’option **créer un nouveau document** est sélectionnée. Pour plus d’informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio ouvre le nouveau classeur Excel dans le concepteur et ajoute le projet **bouton My Excel** à **Explorateur de solutions**.

## <a name="add-controls-to-the-worksheet"></a>Ajouter des contrôles à la feuille de calcul
 Pour cette procédure pas à pas, vous aurez besoin d’un bouton et d’une zone de texte sur la première feuille de calcul.

### <a name="to-add-a-button-and-a-text-box"></a>Pour ajouter un bouton et une zone de texte

1. Vérifiez que le classeur **My Excel Button.xlsx** est ouvert dans le concepteur Visual Studio, avec l' `Sheet1` affichage.

2. Dans l’onglet **contrôles communs** de la boîte à outils, faites glisser un <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> vers `Sheet1` .

3. Dans le menu **affichage** , sélectionnez **fenêtre Propriétés**.

4. Assurez-vous que **TextBox1** est visible dans la zone de liste déroulante de la fenêtre **Propriétés** et remplacez la propriété **nom** de la zone de texte par **texteaffiché**.

5. Faites glisser un contrôle **Button** sur `Sheet1` et modifiez les propriétés suivantes :

   |Propriété|Valeur|
   |--------------|-----------|
   |**Nom**|**insertText**|
   |**Text**|**Insérer du texte**|

   À présent, écrivez le code à exécuter quand l’utilisateur clique sur le bouton.

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Remplir la zone de texte en cas de clic sur le bouton
 Chaque fois que l’utilisateur clique sur le bouton, **Hello World !** est ajouté à la zone de texte.

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Pour écrire dans la zone de texte lorsqu'un clic est effectué

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **Feuil1**, puis cliquez sur **afficher le code** dans le menu contextuel.

2. Ajoutez le code suivant au <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements du bouton :

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#11)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#11)]

3. En C#, vous devez ajouter un gestionnaire d’événements à l' <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> événement, comme indiqué ci-dessous. Pour plus d’informations sur la création de gestionnaires d’événements, consultez [Comment : créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#12)]

## <a name="test-the-application"></a>Test de l’application
 Vous pouvez maintenant tester votre classeur pour vous assurer que le message **Hello World !** apparaît dans la zone de texte lorsque vous cliquez sur le bouton.

### <a name="to-test-your-workbook"></a>Pour tester votre classeur

1. Appuyez sur **F5** pour exécuter votre projet.

2. Cliquez sur le bouton correspondant.

3. Confirmez que **Hello World !** apparaît dans la zone de texte.

## <a name="next-steps"></a>Étapes suivantes
 Cette procédure pas à pas montre les concepts de base de l’utilisation de boutons et de zones de texte dans les feuilles de calcul Excel. Voici quelques tâches susceptibles de venir après :

- Déploiement du projet. Pour plus d’informations, consultez [déployer une solution Office](../vsto/deploying-an-office-solution.md).

- Utilisation des cases à cocher pour modifier la mise en forme. Pour plus d’informations, consultez [procédure pas à pas : modifier la mise en forme des feuilles de calcul à l’aide de contrôles CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>Voir aussi
- [Comment : ajouter des contrôles Windows Forms à des documents Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Procédures pas à pas utilisant Excel](../vsto/walkthroughs-using-excel.md)
- [Limitations des contrôles de Windows Forms sur les documents Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
