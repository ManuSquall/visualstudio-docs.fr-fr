---
title: 'Procédure pas à pas : Modifier la mise en forme du document à l’aide de contrôles CheckBox'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word documents, changing formatting using controls
- documents [Office development in Visual Studio], formatting
- check boxes, Word documents
- documents [Office development in Visual Studio], check box controls
- controls [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 86cf89f7853308e93c55e30deae17786fdb3e413
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863930"
---
# <a name="walkthrough-change-document-formatting-using-checkbox-controls"></a>Procédure pas à pas : Modifier la mise en forme du document à l’aide de contrôles CheckBox
  Cette procédure pas à pas montre comment utiliser des contrôles Windows Forms dans une personnalisation au niveau du document pour Microsoft Office Word pour modifier la mise en forme de texte.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
- Ajout de texte et un contrôle au document dans un projet au niveau du document au moment du design.  
  
- Mise en forme le texte lorsqu’une option est sélectionnée.  
  
  Pour voir le résultat dans un exemple complet, consultez l’exemple des contrôles Word [exemples de développement Office et des procédures pas à pas](../vsto/office-development-samples-and-walkthroughs.md).  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ou [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="create-the-project"></a>Créer le projet  
 La première étape consiste à créer un projet de document Word.  
  
### <a name="create-a-new-project"></a>Créer un nouveau projet  
  
1.  Créer un projet de Document Word portant le nom **My Word Formatting**. Dans l’Assistant, sélectionnez **créer un nouveau document**.  
  
     Pour plus d’informations, consultez [Comment : les projets Office de créer dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio ouvre le nouveau document Word dans le concepteur et ajoute le **My Word Formatting** projet à **l’Explorateur de solutions**.  
  
## <a name="add-text-and-controls-to-the-word-document"></a>Ajouter du texte et des contrôles au document Word  
 Pour cette procédure pas à pas, ajoutez trois cases à cocher et du texte dans un <xref:Microsoft.Office.Tools.Word.Bookmark> contrôle au document Word. Les cases à cocher présentera des options à l’utilisateur pour mettre en forme le texte.  
  
### <a name="add-three-check-boxes"></a>Ajoutez trois cases à cocher  
  
1.  Vérifiez que le document est ouvert dans le concepteur Visual Studio.  
  
2.  À partir de la **contrôles communs** onglet de la **boîte à outils**, faites glisser le premier <xref:Microsoft.Office.Tools.Word.Controls.CheckBox> contrôle au document.  
  
3.  Dans la fenêtre **Propriétés** , changez les propriétés suivantes.  
  
    |Propriété|Value|  
    |--------------|-----------|  
    |**Name**|**applyBoldFont**|  
    |**Text**|**Gras**|  
  
4.  Appuyez sur **entrée** pour déplacer le point d’insertion sous la première case à cocher.  
  
5.  Ajoutez une deuxième case à cocher au document sous la `ApplyBoldFont` case à cocher et modifiez les propriétés suivantes.  
  
    |Propriété|Value|  
    |--------------|-----------|  
    |**Name**|**applyItalicFont**|  
    |**Text**|**Italique**|  
  
6.  Appuyez sur **entrée** pour déplacer le point d’insertion sous la deuxième case à cocher.  
  
7.  Ajoutez une troisième case à cocher au document sous la `ApplyItalicFont` case à cocher et modifiez les propriétés suivantes.  
  
    |Propriété|Value|  
    |--------------|-----------|  
    |**Name**|**applyUnderlineFont**|  
    |**Text**|**Trait de soulignement**|  
  
### <a name="add-text-and-a-bookmark-control"></a>Ajouter du texte et un contrôle Bookmark  
  
1. Déplacer le point d’insertion sous les contrôles de case à cocher et tapez le texte suivant :  
  
    **Cliquez sur une case à cocher pour modifier la mise en forme du texte.**  
  
2. À partir de la **contrôles Word** onglet de la **boîte à outils**, faites glisser un <xref:Microsoft.Office.Tools.Word.Bookmark> contrôle au document.  
  
    Le **ajouter un contrôle Bookmark** boîte de dialogue s’affiche.  
  
3. Sélectionnez le texte que vous avez ajouté au document et cliquez sur **OK**.  
  
    Un <xref:Microsoft.Office.Tools.Word.Bookmark> contrôle nommé **Bookmark1** est ajouté au texte sélectionné dans le document.  
  
4. Dans le **propriétés** fenêtre, modifiez la valeur de la **(nom)** propriété **par fontText.**  
  
   Ensuite, écrivez le code pour mettre en forme le texte lorsqu’une case à cocher est activée ou désactivée.  
  
## <a name="format-the-text-when-a-check-box-is-checked-or-cleared"></a>Mettre en forme le texte lorsqu’une case à cocher est activée ou désactivée  
 Lorsque l’utilisateur sélectionne une option de mise en forme, modifiez le format du texte dans le document.  
  
### <a name="change-formatting-when-a-check-box-is-selected"></a>Modifier la mise en forme lors d’une case à cocher est sélectionnée.  
  
1.  Avec le bouton droit `ThisDocument` dans **l’Explorateur de solutions**, puis cliquez sur **afficher le Code** dans le menu contextuel.  
  
2.  Pour C# uniquement, ajoutez les constantes suivantes à la **ThisDocument** classe.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#2)]  
  
3.  Ajoutez le code suivant à la <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements de la `applyBoldFont` case à cocher.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#3)]  
  
4.  Ajoutez le code suivant à la <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements de la `applyItalicFont` case à cocher.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#4)]  
  
5.  Ajoutez le code suivant à la <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements de la `applyUnderlineFont` case à cocher.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#5)]  
  
6.  Dans C#, vous devez ajouter des gestionnaires d’événements pour les zones de texte pour le <xref:Microsoft.Office.Tools.Word.Document.Startup> événement. Pour plus d’informations sur la création de gestionnaires d’événements, consultez [Comment : créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#6)]  
  
## <a name="test-the-application"></a>Tester l’application  
 Vous pouvez maintenant tester votre document pour vérifier que le texte est mis en forme correctement lorsque vous activez ou désactivez une case à cocher.  
  
### <a name="test-your-document"></a>Tester votre document  
  
1.  Appuyez sur **F5** pour exécuter votre projet.  
  
2.  Activez ou désactivez une case à cocher.  
  
3.  Vérifiez que le texte est mis en forme correctement.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Cette procédure pas à pas montre les principes fondamentaux d’à l’aide des cases à cocher et la modification par programme de mise en forme dans les documents Word. Voici quelques tâches susceptibles de venir après :  
  
-   Utiliser un bouton pour renseigner une zone de texte. Pour plus d’informations, consultez [procédure pas à pas : afficher du texte dans une zone de texte dans un document à l’aide d’un bouton](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).  
  
-   Utilisation de cases d'option pour sélectionner des styles de graphique. Pour plus d’informations, consultez [procédure pas à pas : mise à jour d’un graphique dans un document à l’aide de cases d’option](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).  
  

## <a name="see-also"></a>Voir aussi  
 [Procédures pas à pas utilisant Word](../vsto/walkthroughs-using-word.md)   
 [Procédures pas à pas et des exemples de développement office](../vsto/office-development-samples-and-walkthroughs.md)   
 [NamedRange (contrôle)](../vsto/namedrange-control.md)   
 [Limitations des contrôles Windows Forms sur des documents Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  