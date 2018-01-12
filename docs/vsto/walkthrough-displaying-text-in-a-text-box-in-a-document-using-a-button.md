---
title: "Procédure pas à pas : Affichage de texte dans une zone de texte dans un Document à l’aide d’un bouton | Documents Microsoft"
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
helpviewer_keywords: text boxes, displaying text in documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 803dcbe27eedc4b93443a6389b4acf7ee2dc08cf
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button"></a>Procédure pas à pas : affichage de texte dans une zone de texte d'un document à l'aide d'un bouton
  Cette procédure pas à pas montre comment utiliser les boutons et les zones de texte dans une personnalisation au niveau du document pour Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Ajout de contrôles au document Word d'un projet de niveau document au moment du design.  
  
-   Remplissage d'une zone de texte lorsqu'un clic est effectué.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="creating-the-project"></a>Création du projet  
 La première étape consiste à créer un projet de document Word.  
  
#### <a name="to-create-a-new-project"></a>Pour créer un projet  
  
1.  Créer un projet de Document Word portant le nom **mon bouton Word**. Dans l’Assistant, sélectionnez **créer un nouveau document**.  
  
     Pour plus d'informations, consultez [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio ouvre le nouveau document Word dans le concepteur et ajoute le **mon bouton Word** projet **l’Explorateur de solutions**.  
  
## <a name="adding-controls-to-the-word-document"></a>Ajout de contrôles au document Word  
 Les contrôles d'interface utilisateur se composent d'un bouton et une zone de texte dans le document Word.  
  
#### <a name="to-add-a-button-and-a-text-box"></a>Pour ajouter un bouton et une zone de texte  
  
1.  Vérifiez que le document est ouvert dans le concepteur Visual Studio.  
  
2.  À partir de la **contrôles communs** onglet de la **boîte à outils**, faites glisser un <xref:Microsoft.Office.Tools.Word.Controls.TextBox> contrôle au document.  
  
    > [!NOTE]  
    >  Dans Word, les contrôles sont déposés en ligne avec le texte par défaut. Vous pouvez modifier les façon dont les contrôles et les objets de forme sont insérés en modifiant la valeur par défaut sur le **modifier** onglet de la **Options** boîte de dialogue dans Word.  
  
3.  Dans le menu **Affichage** , cliquez sur **Fenêtre Propriétés**.  
  
4.  Rechercher **TextBox1** dans les **propriétés** la liste déroulante de la fenêtre et modifier le **nom** propriété de la zone de texte **displayText**.  
  
5.  Faites glisser un **bouton** contrôle au document et modifiez les propriétés suivantes.  
  
    |Propriété|Value|  
    |--------------|-----------|  
    |**Name**|**insertText**|  
    |**Text**|**Insérer du texte**|  
  
 Vous pouvez maintenant écrire le code qui s'exécute lors d'un clic sur le bouton.  
  
## <a name="populating-the-text-box-when-the-button-is-clicked"></a>Remplissage d'une zone de texte lorsqu'un clic est effectué  
 Chaque fois que l’utilisateur clique sur le bouton, **Hello World !** est ajouté à la zone de texte.  
  
#### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Pour écrire dans la zone de texte lorsqu'un clic est effectué  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit **ThisDocument**, puis cliquez sur **afficher le Code** dans le menu contextuel.  
  
2.  Ajoutez le code suivant au gestionnaire d'événements <xref:System.Windows.Forms.Control.Click> du bouton :  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#7)]  
  
3.  En C#, vous devez ajouter un gestionnaire d'événements du bouton à l'événement <xref:Microsoft.Office.Tools.Word.Document.Startup>. Pour plus d’informations sur la création de gestionnaires d’événements, consultez [Comment : créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#8)]  
  
## <a name="testing-the-application"></a>Test de l'application  
 Vous pouvez maintenant tester votre document pour vous assurer que le message **Hello World !** s’affiche dans la zone de texte lorsque vous cliquez sur le bouton.  
  
#### <a name="to-test-your-document"></a>Pour tester votre document  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Cliquez sur le bouton.  
  
3.  Vérifiez que **Hello World !** s’affiche dans la zone de texte.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Cette procédure pas à pas présente les notions de base de l'utilisation des boutons et des zones de texte dans les documents Word. Voici quelques tâches susceptibles de venir après :  
  
-   Utilisation d'une zone de liste déroulante pour modifier la mise en forme. Pour plus d’informations, consultez [procédure pas à pas : modification de Document mise en forme à l’aide de contrôles CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
-   Utilisation de cases d'option pour sélectionner des styles de graphique. Pour plus d’informations, consultez [procédure pas à pas : mise à jour d’un graphique dans un Document à l’aide de cases d’option](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles Windows Forms dans une vue d’ensemble des Documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Procédures pas à pas utilisant Word](../vsto/walkthroughs-using-word.md)   
 [Procédures pas à pas et des exemples de développement office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Comment : ajouter des contrôles Windows Forms à des Documents Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)  
  
  