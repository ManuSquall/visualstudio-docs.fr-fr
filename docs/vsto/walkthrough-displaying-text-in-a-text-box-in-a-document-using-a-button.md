---
title: "Proc&#233;dure pas&#160;&#224;&#160;pas&#160;: affichage de texte dans une zone de texte d&#39;un document &#224; l&#39;aide d&#39;un bouton"
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
  - "zones de texte, afficher du texte dans des documents"
ms.assetid: 04c54ed7-9f00-4068-aaec-1f3200110116
caps.latest.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 59
---
# Proc&#233;dure pas&#160;&#224;&#160;pas&#160;: affichage de texte dans une zone de texte d&#39;un document &#224; l&#39;aide d&#39;un bouton
  Cette procédure pas à pas montre comment utiliser les boutons et les zones de texte dans une personnalisation au niveau du document pour Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Ajout de contrôles au document Word d'un projet de niveau document au moment du design.  
  
-   Remplissage d'une zone de texte lorsqu'un clic est effectué.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## Création du projet  
 La première étape consiste à créer un projet de document Word.  
  
#### Pour créer un projet  
  
1.  Créez un projet de document Word et appelez\-le Mon bouton Word.  Dans l'Assistant, sélectionnez **Créer un nouveau document**.  
  
     Pour plus d'informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio ouvre le nouveau document Word dans le concepteur et ajoute le projet **Mon bouton Word** à l'**Explorateur de solutions**.  
  
## Ajout de contrôles au document Word  
 Les contrôles d'interface utilisateur se composent d'un bouton et une zone de texte dans le document Word.  
  
#### Pour ajouter un bouton et une zone de texte  
  
1.  Vérifiez que le document est ouvert dans le concepteur Visual Studio.  
  
2.  Sous l'onglet **Contrôles communs** de la **Boîte à outils**, faites glisser un contrôle <xref:Microsoft.Office.Tools.Word.Controls.TextBox> vers le document.  
  
    > [!NOTE]  
    >  Dans Word, les contrôles sont déposés en ligne avec le texte par défaut.  Vous pouvez modifier la façon dont les contrôles et les objets de forme sont insérés en modifiant la valeur par défaut sous l'onglet **Modifier** de la boîte de dialogue **Options** de Word.  
  
3.  Dans le menu **Affichage**, cliquez sur **Fenêtre Propriétés**.  
  
4.  Recherchez **TextBox1** dans la zone déroulante de la fenêtre **Propriétés** et modifiez la propriété **Nom** de la zone de texte en **displayText**.  
  
5.  Faites glisser un contrôle **bouton** vers le document et modifiez les propriétés suivantes.  
  
    |Propriété|Valeur|  
    |---------------|------------|  
    |**Nom**|**insertText**|  
    |**Texte**|Insérer du texte|  
  
 Vous pouvez maintenant écrire le code qui s'exécute lors d'un clic sur le bouton.  
  
## Remplissage d'une zone de texte lorsqu'un clic est effectué  
 Chaque fois que l'utilisateur clique sur le bouton, **Hello World\!** est ajouté à la zone de texte.  
  
#### Pour écrire dans la zone de texte lorsqu'un clic est effectué  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **ThisDocument.vb**, puis cliquez sur **Afficher le code** dans le menu contextuel.  
  
2.  Ajoutez le code suivant au gestionnaire d'événements <xref:System.Windows.Forms.Control.Click> du bouton :  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#7)]  
  
3.  En C\#, vous devez ajouter un gestionnaire d'événements du bouton à l'événement <xref:Microsoft.Office.Tools.Word.Document.Startup>.  Pour plus d'informations sur la création de gestionnaires d'événements, consultez [Comment : créer des gestionnaires d'événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#8)]  
  
## Test de l'application  
 Vous pouvez maintenant tester votre document pour vous assurer que le message **Hello World\!** s'affiche dans la zone de texte lorsque vous cliquez sur le bouton.  
  
#### Pour tester votre document  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Cliquez sur le bouton.  
  
3.  Vérifiez que **Hello World\!** apparaît dans la zone de texte.  
  
## Étapes suivantes  
 Cette procédure pas à pas présente les notions de base de l'utilisation des boutons et des zones de texte dans les documents Word.  Voici quelques tâches susceptibles de venir après :  
  
-   Utilisation d'une zone de liste déroulante pour modifier la mise en forme.  Pour plus d'informations, consultez [Procédure pas à pas : modification de la mise en forme d'un document à l'aide de contrôles CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
-   Utilisation de cases d'option pour sélectionner des styles de graphique.  Pour plus d'informations, consultez [Procédure pas à pas : mise à jour d'un graphique dans un document à l'aide de cases d'option](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).  
  
## Voir aussi  
 [Vue d'ensemble des contrôles Windows Forms dans les documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Procédures pas à pas utilisant Word](../vsto/walkthroughs-using-word.md)   
 [Exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Comment : ajouter des contrôles Windows Forms à des documents Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)  
  
  