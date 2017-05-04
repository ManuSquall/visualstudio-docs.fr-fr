---
title: "Comment&#160;: ajouter un volet Actions &#224; des documents Word ou &#224; des classeurs Excel | Microsoft Docs"
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
ms.assetid: cea3c2b6-9364-4134-b812-50888ad8bd76
caps.latest.revision: 63
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 62
---
# Comment&#160;: ajouter un volet Actions &#224; des documents Word ou &#224; des classeurs Excel
  Pour ajouter un volet Actions dans un document Microsoft Office Word ou un classeur Microsoft Excel, créez d'abord un contrôle utilisateur Windows Forms.  Ensuite, ajoutez le contrôle utilisateur à la propriété d' <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> du champ d' `ThisDocument.ActionsPane` \(Word\) ou du champ d' `ThisWorkbook.ActionsPane` \(Excel\) dans votre projet.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes.  Ces éléments dépendent de l'édition de Visual Studio dont vous disposez et des paramètres que vous utilisez.  Pour plus d’informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Création du contrôle utilisateur  
 La procédure suivante indique comment créer le contrôle utilisateur dans un projet Word ou Excel.  Elle ajoute également un bouton au contrôle utilisateur qui écrit le texte au document ou au classeur lorsqu'un utilisateur clique dessus.  
  
#### Pour créer le contrôle utilisateur  
  
1.  Ouvrez votre projet au niveau de le document Word ou excel dans Visual Studio.  
  
2.  Dans le menu **Projet**, cliquez sur **Ajouter un nouvel élément**.  
  
3.  Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Contrôle de volet Actions**, attribuez\-lui le nom **HelloControl** et cliquez sur **Ajouter**.  
  
    > [!NOTE]  
    >  Vous pouvez ajouter un élément **Contrôle utilisateur** à votre projet.  Les classes générées par les éléments **Contrôle de volet Actions** et **Contrôle utilisateur** sont équivalentes d'un point de vue fonctionnel.  
  
4.  À partir de l'onglet **Windows Forms** de la **Boîte à outils**, faites glisser un contrôle **Button** sur le contrôle.  
  
    > [!NOTE]  
    >  Si le contrôle n'est pas visible dans le concepteur, double\-cliquez sur **HelloControl** dans l'**Explorateur de solutions**.  
  
5.  Ajoutez le code au gestionnaire d'événements d' <xref:System.Windows.Forms.Control.Click> du bouton.  L'exemple suivant montre le code pour un document Microsoft Office Word.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/HelloControl.cs#12)]
     [!code-vb[Trin_VstcoreActionsPaneWord#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/HelloControl.vb#12)]  
  
6.  En C\#, vous devez ajouter un gestionnaire d'événements pour le clic de bouton.  Vous pouvez placer ce code dans le constructeur `HelloControl`, après l'appel à `IntializeComponent`.  
  
     Pour plus d'informations sur la création de gestionnaires d'événements, consultez [Comment : créer des gestionnaires d'événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/HelloControl.cs#13)]  
  
## Ajout du contrôle utilisateur au volet Actions  
 Pour afficher le volet Actions, ajoutez le contrôle utilisateur à la propriété d' <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> du champ d' `ThisDocument.ActionsPane` \(Word\) ou du champ d' `ThisWorkbook.ActionsPane` \(Excel\).  
  
#### Pour ajouter le contrôle utilisateur au volet Actions  
  
1.  Ajoutez le code suivant à la classe d' `ThisDocument` ou d' `ThisWorkbook` comme déclaration au niveau de la classe \(n'ajoutez pas ce code à une méthode\).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreActionsPaneWord#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#14)]  
  
2.  Ajoutez le code suivant au gestionnaire d'événements d' `ThisDocument_Startup` de la classe d' `ThisDocument` ou au gestionnaire d'événements d' `ThisWorkbook_Startup` de la classe d' `ThisWorkbook` .  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreActionsPaneWord#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#15)]  
  
## Voir aussi  
 [Vue d'ensemble du volet Actions](../vsto/actions-pane-overview.md)   
 [Procédure pas à pas : Insertion de texte dans un document à partir d'un volet Actions](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Comment : gérer la disposition des contrôles dans les volets Actions](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Procédure pas à pas : Insertion de texte dans un document à partir d'un volet Actions](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  