---
title: "Procédure pas à pas : Collecte de données à l’aide d’un Windows Form | Documents Microsoft"
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
- data [Office development in Visual Studio], Windows Forms
- Windows Forms [Office development in Visual Studio], collecting data
- forms [Office development in Visual Studio], walkthroughs
- worksheets [Office development in Visual Studio], collecting data
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2c6945d4e44a0ecb56c6ae7a3823dc0d7951f197
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-collecting-data-using-a-windows-form"></a>Procédure pas à pas : collecte de données à l'aide d'un Windows Form
  Cette procédure pas à pas montre comment ouvrir un Windows Form à partir d’une personnalisation au niveau du document pour Microsoft Office Excel, recueillir des informations auprès de l’utilisateur et écrire ces informations dans une cellule de feuille de calcul.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Bien que cette procédure pas à pas utilise spécifiquement un projet au niveau du document pour Excel, les concepts présentés ici s’appliquent également à d’autres projets Office.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l’interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L’édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="creating-a-new-project"></a>Création d'un projet  
 La première étape consiste à créer un projet de classeur Excel.  
  
#### <a name="to-create-a-new-project"></a>Pour créer un projet  
  
1.  Créez un projet de classeur Excel nommé **WinFormInput**, puis sélectionnez **Créer un nouveau document** dans l’Assistant. Pour plus d'informations, consultez [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio ouvre le nouveau classeur Excel dans le concepteur et ajoute le projet **WinFormInput** à l’ **Explorateur de solutions**.  
  
## <a name="adding-a-namedrange-control-to-the-worksheet"></a>Ajout d’un contrôle NamedRange à la feuille de calcul  
  
#### <a name="to-add-a-named-range-to-sheet1"></a>Pour ajouter une plage nommée à Sheet1  
  
1.  Sélectionnez la cellule **A1** sur `Sheet1`.  
  
2.  Dans la zone **Nom** , tapez **formInput**.  
  
     La zone **Nom** se trouve à gauche de la barre de formule, juste au-dessus de la colonne **A** de la feuille de calcul.  
  
3.  Appuyez sur Entrée.  
  
     Un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> est ajouté à la cellule **A1**. Il n’existe aucune indication visible sur la feuille de calcul, mais **formInput** apparaît dans la zone **Nom** (juste au-dessus de la feuille de calcul sur le côté gauche) et dans la fenêtre **Propriétés** quand la cellule **A1** est sélectionnée.  
  
## <a name="adding-a-windows-form-to-the-project"></a>Ajout d’un Windows Form au projet  
 Créez un Windows Form pour inviter l’utilisateur à fournir des informations.  
  
#### <a name="to-add-a-windows-form"></a>Pour ajouter un Windows Form  
  
1.  Sélectionnez le projet **WinFormInput** dans l’ **Explorateur de solutions**.  
  
2.  Dans le menu **Projet** , cliquez sur **Ajouter un formulaire Windows**.  
  
3.  Nommez le formulaire **GetInputString.vb** ou **GetInputString.cs**, puis cliquez sur **Ajouter**.  
  
     Le nouveau formulaire s’ouvre dans le concepteur.  
  
4.  Ajoutez un <xref:System.Windows.Forms.TextBox> et un <xref:System.Windows.Forms.Button> au formulaire.  
  
5.  Sélectionnez le bouton, recherchez la propriété **Texte** dans la fenêtre **Propriétés** et remplacez le texte par **OK**.  
  
 Ajoutez ensuite du code à `ThisWorkbook.vb` ou `ThisWorkbook.cs` pour recueillir des informations auprès de l’utilisateur.  
  
## <a name="displaying-the-windows-form-and-collecting-information"></a>Affichage du Windows Form et collecte d’informations  
 Créez une instance du Windows Form `GetInputString` et affichez-la, puis écrivez les informations de l’utilisateur dans une cellule de la feuille de calcul.  
  
#### <a name="to-display-the-form-and-collect-information"></a>Pour afficher le formulaire et recueillir des informations  
  
1.  Cliquez avec le bouton droit sur **ThisWorkbook.vb** ou **ThisWorkbook.cs** dans l’ **Explorateur de solutions**, puis cliquez sur **Afficher le code**.  
  
2.  Dans le gestionnaire d’événements <xref:Microsoft.Office.Tools.Excel.Workbook.Open> de `ThisWorkbook`, ajoutez le code suivant pour déclarer une variable pour le formulaire `GetInputString` puis afficher le formulaire.  
  
    > [!NOTE]  
    >  En C#, vous devez ajouter un gestionnaire d’événements comme indiqué dans l’événement <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> ci-dessous. Pour plus d’informations sur la création de gestionnaires d’événements, consultez [Comment : créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#1](../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs#1)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#1](../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb#1)]  
  
3.  Créez une méthode nommée `WriteStringToCell` qui écrit du texte dans une plage nommée. Cette méthode est appelée à partir du formulaire et l’entrée de l’utilisateur est passée au contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> , `formInput`, sur la cellule **A1**.  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#2](../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs#2)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#2](../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb#2)]  
  
 Ajoutez ensuite du code au formulaire pour gérer l’événement de clic du bouton.  
  
## <a name="sending-information-to-the-worksheet"></a>Envoi d’informations à la feuille de calcul  
  
#### <a name="to-send-information-to-the-worksheet"></a>Pour envoyer des informations à la feuille de calcul  
  
1.  Cliquez avec le bouton droit sur **GetInputString** dans l’ **Explorateur de solutions**, puis cliquez sur **Concepteur de vues**.  
  
2.  Double-cliquez sur le bouton pour ouvrir le fichier de code où le gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> du bouton est ajouté.  
  
3.  Ajoutez du code au gestionnaire d’événements pour prendre l’entrée de la zone de texte, l’envoyer à la fonction `WriteStringToCell`, puis fermer le formulaire.  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#3](../vsto/codesnippet/CSharp/WinFormInputCS/GetInputString.cs#3)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#3](../vsto/codesnippet/VisualBasic/WinFormInput/GetInputString.vb#3)]  
  
## <a name="testing"></a>Test  
 Vous pouvez maintenant exécuter le projet. Le Windows Form s’affiche et votre entrée apparaît dans la feuille de calcul.  
  
#### <a name="to-test-your-workbook"></a>Pour tester votre classeur  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Vérifiez que le Windows Form s’affiche.  
  
3.  Tapez **Hello World** dans la zone de texte, puis cliquez sur **OK**.  
  
4.  Vérifiez que **Hello World** apparaît dans la cellule **A1** de la feuille de calcul.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Cette procédure pas à pas présente les notions de base de l’affichage d’un Windows Form et du passage de données à une feuille de calcul. Voici quelques autres tâches que vous pourriez souhaiter effectuer :  
  
-   Utiliser des contrôles Windows Forms sur un classeur Excel ou un document Word. Pour plus d'informations, consultez [Windows Forms Controls on Office Documents Overview](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
-   Modifier l’interface utilisateur d’une application Microsoft Office à partir d’une personnalisation au niveau du document ou d’un complément VSTO. Pour plus d’informations, consultez [personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Développement de Solutions Office](../vsto/developing-office-solutions.md)   
 [Écriture de Code dans les Solutions Office](../vsto/writing-code-in-office-solutions.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Programmation des personnalisations au niveau du Document](../vsto/programming-document-level-customizations.md)   
 [Procédures pas à pas utilisant Word](../vsto/walkthroughs-using-word.md)   
 [Procédures pas à pas utilisant Excel](../vsto/walkthroughs-using-excel.md)  
  
  