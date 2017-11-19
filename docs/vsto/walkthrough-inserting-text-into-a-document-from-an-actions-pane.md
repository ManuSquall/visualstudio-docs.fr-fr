---
title: "Procédure pas à pas : Insertion de texte dans un Document à partir d’un volet Actions | Documents Microsoft"
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
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
ms.assetid: fd14c896-5737-4a20-94f7-6064b67112c5
caps.latest.revision: "70"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5ca062823968153d7c8979cb13c0e3d403237be1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-inserting-text-into-a-document-from-an-actions-pane"></a>Procédure pas à pas : Insertion de texte dans un document à partir d'un volet Actions
  Cette procédure pas à pas montre comment créer un volet actions dans un document Microsoft Office Word. Le volet actions contient deux contrôles qui collecter les entrées, puis envoient le texte au document.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Conception d’une interface à l’aide de contrôles Windows Forms sur un contrôle de volet actions.  
  
-   Affichage du volet actions lorsque l’application s’ouvre.  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ou [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Création du projet  
 La première étape consiste à créer un projet de document Word.  
  
#### <a name="to-create-a-new-project"></a>Pour créer un projet  
  
1.  Créer un projet de Document Word portant le nom **Mon volet Actions de base**. Dans l’Assistant, sélectionnez **créer un nouveau document**. Pour plus d'informations, consultez [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio ouvre le nouveau document Word dans le concepteur et ajoute le **Mon volet Actions de base** projet **l’Explorateur de solutions**.  
  
## <a name="adding-text-and-bookmarks-to-the-document"></a>Ajout de texte et signets au Document  
 Le volet actions enverra le texte aux signets dans le document. Pour concevoir le document, tapez du texte pour créer un formulaire de base.  
  
#### <a name="to-add-text-to-your-document"></a>Pour ajouter du texte à votre document  
  
1.  Tapez le texte suivant dans votre document Word :  
  
     **21 mars 2008**  
  
     **Nom**  
  
     **Adresse**  
  
     **Il s’agit d’un exemple d’un volet actions de base dans Word.**  
  
 Vous pouvez ajouter un <xref:Microsoft.Office.Tools.Word.Bookmark> contrôle à votre document en le faisant glisser à partir de la **boîte à outils** dans Visual Studio ou à l’aide de la **signet** boîte de dialogue dans Word.  
  
#### <a name="to-add-a-bookmark-control-to-your-document"></a>Pour ajouter un contrôle Bookmark à votre document  
  
1.  À partir de la **des contrôles Word** onglet de la **boîte à outils**, faites glisser un <xref:Microsoft.Office.Tools.Word.Bookmark> contrôle à votre document.  
  
     Le **ajouter un contrôle Bookmark** boîte de dialogue s’affiche.  
  
2.  Sélectionner le mot **nom**, sans sélectionner la marque de paragraphe, puis cliquez sur **OK**.  
  
    > [!NOTE]  
    >  La marque de paragraphe doit être en dehors du signet. Si les marques de paragraphe ne sont pas visibles dans le document, cliquez sur le **outils** menu, pointez sur **outils Microsoft Office Word** puis cliquez sur **Options**. Cliquez sur le **vue** et sélectionnez le **marques de paragraphe** case à cocher dans la **marques** section de la **Options** boîte de dialogue.  
  
3.  Dans le **propriétés** fenêtre, de modifier le **nom** propriété de **Bookmark1** à **showName**.  
  
4.  Sélectionner le mot **adresse**, sans sélectionner la marque de paragraphe.  
  
5.  Sur le **insérer** onglet du ruban, dans le **liens** , cliquez sur **signet**.  
  
6.  Dans le **signet** boîte de dialogue, tapez **showAddress** dans les **nom du signet** , puis cliquez sur **ajouter**.  
  
## <a name="adding-controls-to-the-actions-pane"></a>Ajout de contrôles au volet Actions  
 Pour concevoir l’interface du volet actions, ajoutez un contrôle de volet actions au projet, puis ajoutez les contrôles Windows Forms au contrôle de volet actions.  
  
#### <a name="to-add-an-actions-pane-control"></a>Pour ajouter un contrôle de volet actions  
  
1.  Sélectionnez le **Mon volet Actions de base** projet **l’Explorateur de solutions**.  
  
2.  Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.  
  
3.  Dans le **ajouter un nouvel élément** boîte de dialogue, cliquez sur **contrôle de volet Actions**, nommez le contrôle **InsertTextControl** et cliquez sur **ajouter**.  
  
#### <a name="to-add-windows-form-controls-to-the-actions-pane-control"></a>Pour ajouter des contrôles Windows Form au contrôle de volet actions  
  
1.  Si le contrôle de volet actions n’est pas visible dans le concepteur, double-cliquez sur **InsertTextControl**.  
  
2.  À partir de la **contrôles communs** onglet de la **boîte à outils**, faites glisser un **étiquette** vers le contrôle de volet actions.  
  
3.  Modifier la **texte** propriété du contrôle Label pour **nom**.  
  
4.  Ajouter un **zone de texte** le contrôle à un contrôle de volet actions et modifiez les propriétés suivantes.  
  
    |Propriété|Valeur|  
    |--------------|-----------|  
    |**Nom**|**getName**|  
    |**Taille**|**130, 20**|  
  
5.  Ajoutez un deuxième **étiquette** le contrôle à un contrôle de volet actions et modifiez le **texte** propriété **adresse**.  
  
6.  Ajoutez un deuxième **zone de texte** le contrôle à un contrôle de volet actions et modifiez les propriétés suivantes.  
  
    |Propriété|Valeur|  
    |--------------|-----------|  
    |**Nom**|**getAddress**|  
    |**Accepte le retour**|**True**|  
    |**Multiline**|**True**|  
    |**Taille**|**130, 40**|  
  
7.  Ajouter un **bouton** le contrôle à un contrôle de volet actions et modifiez les propriétés suivantes.  
  
    |Propriété|Valeur|  
    |--------------|-----------|  
    |**Nom**|**addText**|  
    |**Text**|**INSERT**|  
  
## <a name="adding-code-to-insert-text-into-the-document"></a>Ajout de Code pour insérer du texte dans le Document  
 Dans le volet actions, écrire du code qui insère le texte dans les zones de texte appropriées <xref:Microsoft.Office.Tools.Word.Bookmark> contrôles dans le document. Vous pouvez utiliser la `Globals` classe pour accéder aux contrôles dans le document à partir des contrôles dans le volet actions. Pour plus d’informations, consultez [accès Global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
#### <a name="to-insert-text-from-the-actions-pane-in-a-bookmark-in-the-document"></a>Pour insérer du texte dans le volet actions dans un signet dans le document  
  
1.  Ajoutez le code suivant à la <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements de la **addText** bouton.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#8)]
     [!code-vb[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/InsertTextControl.vb#8)]  
  
2.  En c#, vous devez ajouter un gestionnaire d’événements pour le clic de bouton. Vous pouvez placer ce code dans le `InsertTextControl` constructeur après l’appel à `IntializeComponent`. Pour plus d’informations sur la création de gestionnaires d’événements, consultez [Comment : créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#9)]  
  
## <a name="adding-code-to-show-the-actions-pane"></a>Ajout de Code pour afficher le volet Actions  
 Pour afficher le volet actions, ajoutez le contrôle que vous avez créé à la collection.  
  
#### <a name="to-show-the-actions-pane"></a>Pour afficher le volet actions  
  
1.  Créer une nouvelle instance du contrôle de volet actions dans la `ThisDocument` classe.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#10)]  
  
2.  Ajoutez le code suivant à la <xref:Microsoft.Office.Tools.Word.Document.Startup> Gestionnaire d’événements de `ThisDocument`.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#11)]  
  
## <a name="testing-the-application"></a>Test de l'application  
 Tester votre document pour vérifier que le volet actions s’ouvre lorsque le document est ouvert et que le texte tapé dans les zones de texte est inséré dans les signets lorsque le bouton est activé.  
  
#### <a name="to-test-your-document"></a>Pour tester votre document  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
2.  Vérifiez que le volet actions est visible.  
  
3.  Tapez votre nom et l’adresse dans les zones de texte dans le volet actions, cliquez sur **insérer**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Voici quelques tâches susceptibles de venir après :  
  
-   Création d’un volet actions dans Excel. Pour plus d’informations, consultez [Comment : ajouter un volet Actions à des classeurs Excel](http://msdn.microsoft.com/en-us/62abfce6-e44f-419d-85d8-26bf59f33872).  
  
-   Liaison de données aux contrôles dans un volet actions. Pour plus d’informations, consultez [procédure pas à pas : liaison de données aux contrôles dans un volet Actions Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du volet Actions](../vsto/actions-pane-overview.md)   
 [Comment : ajouter un volet Actions à des Documents Word ou des classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Comment : ajouter un volet Actions à des classeurs Excel](http://msdn.microsoft.com/en-us/62abfce6-e44f-419d-85d8-26bf59f33872)   
 [Comment : gérer la disposition des contrôles dans les volets Actions](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Bookmark, contrôle](../vsto/bookmark-control.md)  
  
  