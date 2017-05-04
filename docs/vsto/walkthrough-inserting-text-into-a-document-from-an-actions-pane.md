---
title: "Proc&#233;dure pas &#224; pas : Insertion de texte dans un document &#224; partir d&#39;un volet Actions | Microsoft Docs"
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
  - "volets Actions (développement Office dans Visual Studio), ajouter des contrôles"
  - "volets Actions (développement Office dans Visual Studio), créer dans Word"
  - "documents dynamiques (développement Office dans Visual Studio), ajouter des contrôles"
  - "documents dynamiques (développement Office dans Visual Studio), créer dans Word"
ms.assetid: fd14c896-5737-4a20-94f7-6064b67112c5
caps.latest.revision: 70
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 69
---
# Proc&#233;dure pas &#224; pas : Insertion de texte dans un document &#224; partir d&#39;un volet Actions
  Cette procédure pas à pas montre la création d'un volet Actions dans un document Microsoft Office Word.  Le volet Actions contient deux contrôles qui recueillent l'entrée puis envoient le texte au document.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Conception d'une interface en utilisant des contrôles Windows Forms sur un contrôle de volet Actions.  
  
-   Affichage du volet Actions lors de l'ouverture de l'application.  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes.  Ces éléments dépendent de l'édition de Visual Studio dont vous disposez et des paramètres que vous utilisez.  Pour plus d’informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ou [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## Création du projet  
 La première étape consiste à créer un projet de document Word.  
  
#### Pour créer un projet  
  
1.  Créez un projet de document Word et attribuez\-lui le nom My Basic Actions Pane.  Dans l'Assistant, sélectionnez **Créer un nouveau document**.  Pour plus d’informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio ouvre le nouveau document Word dans le concepteur et ajoute le projet **My Basic Actions Pane** à l'**Explorateur de solutions**.  
  
## Ajout de texte et de signets au document  
 Le volet Actions enverra le texte aux signets dans le document.  Pour concevoir le document, tapez du texte pour créer un formulaire de base.  
  
#### Pour ajouter du texte à votre document  
  
1.  Tapez le texte suivant dans votre document Word :  
  
     March 21, 2008  
  
     Nom  
  
     Adresse  
  
     Il s'agit d'un exemple de volet Actions de base dans Word.  
  
 Vous pouvez ajouter un contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> dans votre document en le faisant glisser à partir de la **Boîte à outils** dans Visual Studio ou en utilisant la boîte de dialogue **Signet** dans Word.  
  
#### Pour ajouter un contrôle Bookmark à votre document  
  
1.  À partir de l'onglet **Contrôles Word** de la **Boîte à outils**, faites glisser un contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> vers votre document.  
  
     La boîte de dialogue **Ajouter un contrôle Bookmark** s'affiche.  
  
2.  Sélectionnez le mot **Name**, sans sélectionner la marque de paragraphe, et cliquez sur **OK**.  
  
    > [!NOTE]  
    >  La marque de paragraphe doit être en dehors du signet.  Si les marques de paragraphe ne sont pas visibles dans le document, cliquez sur le menu **Outils**, pointez sur **Outils Microsoft Office Word**, puis cliquez sur **Options**.  Cliquez sur l'onglet **Affichage** et activez la case à cocher **Marques de paragraphe** dans la section **Marques de format** de la boîte de dialogue **Options**.  
  
3.  Dans la fenêtre **Propriétés**, remplacez la propriété **Name** de **Bookmark1** par **showName**.  
  
4.  Sélectionnez le mot **Address**, sans sélectionner la marque de paragraphe.  
  
5.  Sous l'onglet **Insérer** du ruban, dans le groupe **Liens**, cliquez sur **Signet**.  
  
6.  Dans la boîte de dialogue **Signet**, tapez **showAddress** dans la zone **Nom du signet** et cliquez sur **Ajouter**.  
  
## Ajout de contrôles au volet Actions  
 Pour concevoir l'interface du volet Actions, ajoutez un contrôle de volet Actions au projet, puis ajoutez les contrôles Windows Forms au contrôle de volet Actions.  
  
#### Pour ajouter un contrôle de volet Actions  
  
1.  Sélectionnez le projet **My Basic Actions Pane** dans l'**Explorateur de solutions**.  
  
2.  Dans le menu **Projet**, cliquez sur **Ajouter un nouvel élément**.  
  
3.  Dans la boîte de dialogue **Ajouter un nouvel élément**, cliquez sur **Contrôle de volet Actions**, nommez le contrôle **InsertTextControl** et cliquez sur **Ajouter**.  
  
#### Pour ajouter des contrôles Windows Form au contrôle de volet Actions  
  
1.  Si le contrôle de volet Actions n'est pas visible dans le concepteur, double\-cliquez sur **InsertTextControl**.  
  
2.  À partir de l'onglet **Contrôles communs** de la **Boîte à outils**, faites glisser un contrôle **Label** vers le contrôle de volet Actions.  
  
3.  Remplacez la propriété **Text** du contrôle Label par **Name**.  
  
4.  Ajoutez un contrôle **Textbox** au contrôle de volet Actions et modifiez les propriétés suivantes.  
  
    |Propriété|Valeur|  
    |---------------|------------|  
    |**Nom**|**getName**|  
    |**Taille**|**130, 20**|  
  
5.  Ajoutez un deuxième contrôle **Label** au contrôle de volet Actions et remplacez la propriété **Text** par **Address**.  
  
6.  Ajoutez un deuxième contrôle **Textbox** au contrôle de volet Actions et modifiez les propriétés suivantes.  
  
    |Propriété|Valeur|  
    |---------------|------------|  
    |**Nom**|**getAddress**|  
    |**Accepts Return**|**True**|  
    |**Multiline**|**True**|  
    |**Taille**|**130, 40**|  
  
7.  Ajoutez un contrôle **Button** au contrôle de volet Actions et modifiez les propriétés suivantes.  
  
    |Propriété|Valeur|  
    |---------------|------------|  
    |**Nom**|**addText**|  
    |**du texte ;**|**Insert**|  
  
## Ajout de code pour insérer du texte dans le document  
 Dans le volet Actions, écrivez un code qui insère le texte des zones de texte dans les contrôles <xref:Microsoft.Office.Tools.Word.Bookmark> appropriés dans le document.  Vous pouvez utiliser la classe `Globals` pour accéder aux contrôles du document à partir des contrôles du volet Actions.  Pour plus d’informations, consultez [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
#### Pour insérer le texte du volet Actions dans un signet dans le document  
  
1.  Ajoutez le code suivant au gestionnaire d'événements <xref:System.Windows.Forms.Control.Click> du bouton **addText**.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/InsertTextControl.cs#8)]
     [!code-vb[Trin_VstcoreActionsPaneWord#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/InsertTextControl.vb#8)]  
  
2.  En C\#, vous devez ajouter un gestionnaire d'événements pour le clic de bouton.  Vous pouvez placer ce code dans le constructeur `InsertTextControl`, après l'appel à `IntializeComponent`.  Pour plus d'informations sur la création de gestionnaires d'événements, consultez [Comment : créer des gestionnaires d'événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/InsertTextControl.cs#9)]  
  
## Ajout de code pour afficher le volet Actions  
 Pour afficher le volet Actions, ajoutez le contrôle créé à la collection de contrôles.  
  
#### Pour afficher le volet Actions  
  
1.  Créez une instance du contrôle de volet Actions dans la classe `ThisDocument`.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreActionsPaneWord#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#10)]  
  
2.  Ajoutez le code suivant au gestionnaire d'événements <xref:Microsoft.Office.Tools.Word.Document.Startup> de la classe `ThisDocument`.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneWord#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#11)]  
  
## Test de l'application  
 Testez votre document pour vérifier que le volet Actions s'ouvre lorsque le document est ouvert et que le texte tapé dans les zones de texte est inséré dans les signets lorsqu'un utilisateur clique sur le bouton.  
  
#### Pour tester votre document  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Vérifiez que le volet Actions est visible.  
  
3.  Tapez votre nom et votre adresse dans les zones de texte sur le volet Actions et cliquez sur **Insérer**.  
  
## Étapes suivantes  
 Vous devrez peut\-être ensuite exécuter les opérations suivantes :  
  
-   Création d'un volet Actions dans Excel.  Pour plus d’informations, consultez [How to: Add an Actions Pane to Excel Workbooks](http://msdn.microsoft.com/fr-fr/62abfce6-e44f-419d-85d8-26bf59f33872).  
  
-   Liaison de données aux contrôles d'un volet Actions  Pour plus d’informations, consultez [Procédure pas à pas : liaison de données aux contrôles dans un volet Actions Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).  
  
## Voir aussi  
 [Vue d'ensemble du volet Actions](../vsto/actions-pane-overview.md)   
 [Comment : ajouter un volet Actions à des documents Word ou à des classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [How to: Add an Actions Pane to Excel Workbooks](http://msdn.microsoft.com/fr-fr/62abfce6-e44f-419d-85d8-26bf59f33872)   
 [Comment : gérer la disposition des contrôles dans les volets Actions](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Bookmark, contrôle](../vsto/bookmark-control.md)  
  
  