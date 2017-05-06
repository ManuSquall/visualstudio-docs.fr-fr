---
title: "Proc&#233;dure pas &#224; pas&#160;: modification de la mise en forme d&#39;un document &#224; l&#39;aide de contr&#244;les CheckBox"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "cases à cocher, documents Word"
  - "contrôles (développement Office dans Visual Studio), ajouter à des documents"
  - "documents (développement Office dans Visual Studio), contrôles check box"
  - "documents (développement Office dans Visual Studio), mettre en forme"
  - "documents Word, modifier la mise en forme à l'aide de contrôles"
ms.assetid: 3740e41d-a57e-43bb-87e7-6e5481ef290b
caps.latest.revision: 70
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 69
---
# Proc&#233;dure pas &#224; pas&#160;: modification de la mise en forme d&#39;un document &#224; l&#39;aide de contr&#244;les CheckBox
  Cette procédure pas à pas montre comment utiliser des contrôles Windows Forms dans une personnalisation au niveau du document pour Microsoft Office Word, afin de modifier la mise en forme du texte.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Ajout de texte et d'un contrôle au document dans un projet au niveau du document au moment du design.  
  
-   Mise en forme du texte lorsqu'une option est sélectionnée.  
  
 Pour consulter le résultat sous forme d'exemple terminé, consultez les exemples de contrôles Word dans [Exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ou [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## Création du projet  
 La première étape consiste à créer un projet de document Word.  
  
#### Pour créer un projet  
  
1.  Créez un projet de document Word et appelez\-le My Word Formatting.  Dans l'Assistant, sélectionnez **Créer un nouveau document**.  
  
     Pour plus d’informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio ouvre le nouveau document Word dans le concepteur et ajoute le projet **My Word Formatting** à l'**Explorateur de solutions**.  
  
## Ajout de texte et de contrôles au document Word  
 Pour cette procédure pas à pas, ajoutez trois cases à cocher et du texte dans un contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> au document Word.  Les cases à cocher présenteront des options à l'utilisateur pour mettre en forme le texte.  
  
#### Pour ajouter trois cases à cocher  
  
1.  Vérifiez que le document est ouvert dans le concepteur Visual Studio.  
  
2.  À partir de l'onglet **Contrôles communs** de la **Boîte à outils**, faites glisser le premier contrôle <xref:Microsoft.Office.Tools.Word.Controls.CheckBox> sur le document.  
  
3.  Dans la fenêtre **Propriétés**, modifiez les propriétés suivantes.  
  
    |Propriété|Valeur|  
    |---------------|------------|  
    |**Nom**|**applyBoldFont**|  
    |**du texte ;**|Bold|  
  
4.  Appuyez sur **Entrée** pour déplacer le point d'insertion sous la première case à cocher.  
  
5.  Ajoutez une deuxième case à cocher au document sous la case à cocher `ApplyBoldFont` et modifiez les propriétés suivantes :  
  
    |Propriété|Valeur|  
    |---------------|------------|  
    |**Nom**|**applyItalicFont**|  
    |**du texte ;**|Italique|  
  
6.  Appuyez sur **Entrée** pour déplacer le point d'insertion sous la deuxième case à cocher.  
  
7.  Ajoutez une troisième case à cocher au document sous la case à cocher `ApplyItalicFont` et modifiez les propriétés suivantes.  
  
    |Propriété|Valeur|  
    |---------------|------------|  
    |**Nom**|**applyUnderlineFont**|  
    |**du texte ;**|Souligné|  
  
#### Pour ajouter du texte et un contrôle Bookmark  
  
1.  Déplacez le point d'insertion sous les contrôles des cases à cocher et tapez le texte suivant :  
  
     Activez une case à cocher pour modifier la mise en forme de ce texte.  
  
2.  À partir de l'onglet **Contrôles Word** de la **Boîte à outils**, faites glisser un contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> sur le document.  
  
     La boîte de dialogue **Ajouter un contrôle Bookmark** s'affiche.  
  
3.  Sélectionnez le texte que vous avez ajouté au document et cliquez sur **OK**.  
  
     Un contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> nommé **Bookmark1** est ajouté au texte sélectionné dans le document.  
  
4.  Dans la fenêtre **Propriétés**, remplacez la valeur de la propriété **\(Nom\)** par **fontText.**  
  
 Ensuite, écrivez le code pour que le texte soit mis en forme lorsqu'une case à cocher est activée ou désactivée.  
  
## Mise en forme du texte lorsqu'une case à cocher est activée ou désactivée  
 Lorsque l'utilisateur sélectionne une option de mise en forme, modifiez la mise en forme du texte dans le document.  
  
#### Pour modifier la mise en forme lorsqu'une case à cocher est activée  
  
1.  Cliquez avec le bouton droit sur `ThisDocument` dans l'**Explorateur de solutions**, puis cliquez sur **Afficher le code** dans le menu contextuel.  
  
2.  Pour C\# uniquement, ajoutez les constantes suivantes à la classe **ThisDocument**.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#2)]  
  
3.  Ajoutez le code suivant au gestionnaire d'événements <xref:System.Windows.Forms.Control.Click> de la case à cocher `applyBoldFont`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#3)]  
  
4.  Ajoutez le code suivant au gestionnaire d'événements <xref:System.Windows.Forms.Control.Click> de la case à cocher `applyItalicFont`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#4)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#4)]  
  
5.  Ajoutez le code suivant au gestionnaire d'événements <xref:System.Windows.Forms.Control.Click> de la case à cocher `applyUnderlineFont`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#5)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#5)]  
  
6.  En C\#, vous devez ajouter des gestionnaires d'événements pour les zones de texte à l'événement <xref:Microsoft.Office.Tools.Word.Document.Startup>.  Pour plus d'informations sur la création de gestionnaires d'événements, consultez [Comment : créer des gestionnaires d'événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#6)]  
  
## Test de l'application  
 Vous pouvez maintenant tester votre document pour vérifier que le texte est correctement mis en forme lorsque vous activez ou désactivez une case à cocher.  
  
#### Pour tester votre document  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Activez ou désactivez une case à cocher.  
  
3.  Vérifiez que le texte est correctement mis en forme.  
  
## Étapes suivantes  
 Cette procédure pas à pas présente les notions de base de l'utilisation des cases à cocher et de la modification par programmation de la mise en forme du texte dans les documents Word.  Vous devrez peut\-être ensuite exécuter les opérations suivantes :  
  
-   Utilisez un bouton pour remplir une zone de texte.  Pour plus d’informations, consultez [Procédure pas à pas : affichage de texte dans une zone de texte d'un document à l'aide d'un bouton](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).  
  
-   Utilisation de cases d'option pour sélectionner des styles de graphique.  Pour plus d’informations, consultez [Procédure pas à pas : mise à jour d'un graphique dans un document à l'aide de cases d'option](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).  
  
## Voir aussi  
 [Procédures pas à pas utilisant Word](../vsto/walkthroughs-using-word.md)   
 [Exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [NamedRange, contrôle](../vsto/namedrange-control.md)   
 [Limitations des contrôles Windows Forms dans les documents Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  