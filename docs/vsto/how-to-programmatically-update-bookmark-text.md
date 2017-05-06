---
title: "Comment&#160;: mettre &#224; jour le texte d&#39;un signet par programmation"
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
  - "Bookmark (contrôle), mettre à jour le contenu"
  - "signets, mettre à jour le texte"
  - "texte (développement Office dans Visual Studio), mettre à jour des signets"
ms.assetid: 2324164d-2538-4695-9aaf-7285ce403be3
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# Comment&#160;: mettre &#224; jour le texte d&#39;un signet par programmation
  Vous pouvez insérer un texte dans un signet d'espace réservé d'un document Microsoft Office Word afin de pouvoir récupérer le texte ultérieurement, ou pour remplacer le texte d'un signet.  Si vous développez une personnalisation au niveau du document, vous pouvez également mettre à jour le texte dans un contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> lié aux données.  Pour plus d'informations, consultez [Liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 L'objet Bookmark peut être de deux types :  
  
-   Un contrôle hôte <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     Les contrôles <xref:Microsoft.Office.Tools.Word.Bookmark> étendent les objets <xref:Microsoft.Office.Interop.Word.Bookmark> natifs en activant la liaison de données et en exposant les événements.  Pour plus d'informations sur les contrôles hôtes, consultez [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md).  
  
-   Un objet <xref:Microsoft.Office.Interop.Word.Bookmark> natif.  
  
     Les objets <xref:Microsoft.Office.Interop.Word.Bookmark> n'ont pas de fonctionnalités de liaison de données ou d'événements.  
  
 Lorsque vous assignez un texte à un signet, le comportement diffère entre un <xref:Microsoft.Office.Interop.Word.Bookmark> et un <xref:Microsoft.Office.Tools.Word.Bookmark>.  Pour plus d'informations, consultez [Bookmark, contrôle](../vsto/bookmark-control.md).  
  
## Utilisation des contrôles hôtes  
  
#### Pour mettre à jour le contenu d'un signet à l'aide d'un contrôle Bookmark  
  
1.  Créez une procédure qui accepte un argument `bookmark` comme nom du signet et un argument `newText` comme chaîne à attribuer à la propriété <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A>.  
  
    > [!NOTE]  
    >  L'affectation de texte à la propriété <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> ou <xref:Microsoft.Office.Tools.Word.Bookmark.FormattedText%2A> d'un contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> n'entraîne pas la suppression du signet.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#63](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#63)]
     [!code-vb[Trin_VstcoreWordAutomation#63](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#63)]  
  
2.  Affectez la chaîne *newText* à la propriété <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> du <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#64](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#64)]
     [!code-vb[Trin_VstcoreWordAutomation#64](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#64)]  
  
## Utilisation des objets Word  
  
#### Pour mettre à jour le contenu d'un signet à l'aide d'un objet Bookmark Word  
  
1.  Créez une procédure qui accepte un argument `bookmark` comme nom du <xref:Microsoft.Office.Interop.Word.Bookmark> et un argument `newText` comme chaîne à attribuer à la propriété <xref:Microsoft.Office.Interop.Word.Range.Text%2A> du signet.  
  
    > [!NOTE]  
    >  L'assignation de texte à un objet Word <xref:Microsoft.Office.Interop.Word.Bookmark> natif entraîne la suppression du signet.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#65](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#65)]
     [!code-vb[Trin_VstcoreWordAutomation#65](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#65)]  
  
2.  Affectez la chaîne *newText* à la propriété <xref:Microsoft.Office.Interop.Word.Range.Text%2A> du signet, ce qui supprime automatiquement le signet.  Puis, ajoutez de nouveau le signet à la collection <xref:Microsoft.Office.Interop.Word.Bookmarks>.  
  
     L'exemple de code suivant peut être utilisé dans une personnalisation au niveau du document.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#66](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#66)]
     [!code-vb[Trin_VstcoreWordAutomation#66](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#66)]  
  
     L'exemple de code suivant peut être utilisé dans un complément VSTO.  Cet exemple utilise le document actif.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#66](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#66)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#66](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#66)]  
  
## Voir aussi  
 [Comment : insérer du texte dans les documents Word par programmation](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Vue d'ensemble du modèle objet Word](../vsto/word-object-model-overview.md)   
 [Bookmark, contrôle](../vsto/bookmark-control.md)  
  
  