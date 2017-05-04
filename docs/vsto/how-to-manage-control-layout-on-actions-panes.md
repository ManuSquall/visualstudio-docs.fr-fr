---
title: "Comment&#160;: g&#233;rer la disposition des contr&#244;les dans les volets Actions | Microsoft Docs"
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
  - "volets Actions (développement Office dans Visual Studio), disposition des contrôles"
  - "contrôles (développement Office dans Visual Studio), disposition des volets Actions"
  - "documents dynamiques (développement Office dans Visual Studio), disposition des contrôles"
ms.assetid: 857550d0-b9c0-4d2f-a947-dd955bcf2823
caps.latest.revision: 59
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 55
---
# Comment&#160;: g&#233;rer la disposition des contr&#244;les dans les volets Actions
  Un volet Actions est ancré par défaut à droite d'un document ou d'une feuille de calcul ; toutefois, il peut être ancré à gauche, en haut ou en bas.  Si vous utilisez plusieurs contrôles utilisateur, vous pouvez écrire du code pour empiler correctement les contrôles utilisateur sur le volet Actions.  Pour plus d’informations, consultez [Vue d'ensemble du volet Actions](../vsto/actions-pane-overview.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 L'ordre de la pile des contrôles varie suivant que le volet Actions est ancré verticalement ou horizontalement.  
  
> [!NOTE]  
>  Si l'utilisateur redimensionne le volet Actions au moment de l'exécution, vous pouvez définir les contrôles à redimensionner avec le volet Actions.  Vous pouvez utiliser la propriété <xref:System.Windows.Forms.Control.Anchor%2A> d'un contrôle Windows Forms pour ancrer des contrôles au volet Actions.  Pour plus d’informations, consultez [Comment : ancrer des contrôles aux Windows Forms](../Topic/How%20to:%20Anchor%20Controls%20on%20Windows%20Forms.md).  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes.  Ces éléments dépendent de l'édition de Visual Studio dont vous disposez et des paramètres que vous utilisez.  Pour plus d’informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour définir l'ordre de pile des contrôles de volet Actions  
  
1.  Ouvrez un projet au niveau du document pour Microsoft Office Word comprenant un volet Actions avec plusieurs contrôles utilisateur ou contrôles de volet Actions imbriqués.  Pour plus d’informations, consultez [Comment : ajouter un volet Actions à des documents Word ou à des classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
2.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **ThisDocument.cs** ou **ThisDocument.vb**, puis sélectionnez **Afficher le code**.  
  
3.  Dans le gestionnaire d'événements <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged> du volet Actions, vérifiez si l'orientation du volet Actions est horizontale.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#30](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreActionsPaneWord#30](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#30)]  
  
4.  Si l'orientation est horizontale, empilez les contrôles du volet Actions à partir de la gauche ; sinon empilez\-les depuis le haut.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#31](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreActionsPaneWord#31](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#31)]  
  
5.  En C\#, vous devez ajouter un gestionnaire d'événements pour le `ActionsPane` au gestionnaire d'événements <xref:Microsoft.Office.Tools.Word.Document.Startup>.  Pour plus d'informations sur la création de gestionnaires d'événements, consultez [Comment : créer des gestionnaires d'événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#32](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#32)]  
  
6.  Exécutez le projet et vérifiez que les contrôles du volet Actions sont empilés de gauche à droite lorsque le volet Actions est ancré en haut du document, et de haut en bas lorsqu'il est ancré sur le côté droit du document.  
  
## Exemple  
 [!code-csharp[Trin_VstcoreActionsPaneWord#29](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#29)]
 [!code-vb[Trin_VstcoreActionsPaneWord#29](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#29)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Un projet au niveau du document dans Word, comportant un volet Actions, qui contient plusieurs contrôles utilisateur ou contrôles de volet Actions imbriqués.  
  
## Voir aussi  
 [Vue d'ensemble du volet Actions](../vsto/actions-pane-overview.md)   
 [Comment : ajouter un volet Actions à des documents Word ou à des classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Comment : ajouter un volet Actions à des documents Word ou à des classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Procédure pas à pas : Insertion de texte dans un document à partir d'un volet Actions](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Procédure pas à pas : Insertion de texte dans un document à partir d'un volet Actions](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  