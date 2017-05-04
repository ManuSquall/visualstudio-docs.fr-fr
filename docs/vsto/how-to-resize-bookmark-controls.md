---
title: "Comment&#160;: redimensionner les contr&#244;les Bookmark | Microsoft Docs"
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
  - "contrôles (développement Office dans Visual Studio), redimensionnement"
  - "Bookmark (contrôle), redimensionnement"
ms.assetid: 3de1c774-921a-4113-a54a-e3b8d4a65d53
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# Comment&#160;: redimensionner les contr&#244;les Bookmark
  Vous définissez la taille d’un contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> quand vous l’ajoutez à un document Microsoft Office Word. Vous pouvez également le redimensionner ultérieurement.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Il existe trois manières de redimensionner un signet :  
  
-   Ajouter ou supprimer du texte dans le contrôle <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     Quand vous ajoutez du texte dans un signet, la taille du signet augmente automatiquement pour contenir le nouveau texte. Quand vous supprimez du texte, la taille du signet diminue automatiquement.  
  
-   Modifier les propriétés <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> et <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> du contrôle <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     C’est utile si vous ne modifiez la taille que de quelques caractères.  
  
-   Recréer le contrôle <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     C’est utile en cas de modification substantielle de la taille ou de l’emplacement d’un signet.  
  
 Dans les projets au niveau du document, vous pouvez ajouter des contrôles <xref:Microsoft.Office.Tools.Word.Bookmark> au document de votre projet au moment du design ou au moment de l'exécution. Dans les projets de complément VSTO, vous pouvez ajouter des contrôles <xref:Microsoft.Office.Tools.Word.Bookmark> à tout document ouvert au moment de l’exécution. Pour plus d'informations, consultez [Comment : ajouter des contrôles Bookmark à des documents Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Modification des propriétés Start et End  
  
#### Pour redimensionner un signet dans un projet au niveau du document au moment du design  
  
1.  Sélectionnez le signet dans la fenêtre **Propriétés**.  
  
2.  Augmentez ou diminuez la valeur de la propriété <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A>.  
  
3.  Augmentez ou diminuez la valeur de la propriété <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A>.  
  
#### Pour redimensionner un signet dans un projet au niveau du document au moment de l’exécution  
  
1.  Modifiez les propriétés <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> et <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> d’un <xref:Microsoft.Office.Tools.Word.Bookmark> que vous avez créé au moment de l’exécution ou au moment du design.  
  
     L’exemple de code suivant ajoute cinq caractères au début d’un signet nommé `SampleBookmark`. Ce code part du principe qu’il existe au moins cinq caractères de texte avant le signet.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/CS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsWord#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/VB/ThisDocument.vb#2)]  
  
     L’exemple de code suivant ajoute cinq caractères à la fin du même signet. Ce code part du principe qu’il existe au moins cinq caractères de texte après le signet.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/CS/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsWord#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/VB/ThisDocument.vb#3)]  
  
#### Pour redimensionner un signet dans un projet de complément VSTO au moment de l’exécution  
  
1.  Modifiez les propriétés <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> et <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> d’un <xref:Microsoft.Office.Tools.Word.Bookmark> que vous avez créé au moment de l’exécution.  
  
     L’exemple de code suivant crée un <xref:Microsoft.Office.Tools.Word.Bookmark> qui contient le texte du premier paragraphe du document actif, puis il supprime cinq caractères au début et à la fin du <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#16)]
     [!code-vb[Trin_WordAddInDynamicControls#16](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#16)]  
  
## Recréation du signet  
 Vous pouvez redimensionner un signet dans un projet au niveau du document en ajoutant un nouveau signet du même nom que le signet existant, mais avec une taille différente.  
  
#### Pour recréer un signet dans un projet au niveau du document au moment du design  
  
1.  Sélectionnez le texte à inclure dans le nouveau contrôle <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
2.  Dans le menu **Insérer**, cliquez sur **Signet**.  
  
3.  Dans la boîte de dialogue **Signet**, sélectionnez le nom du signet à redimensionner et cliquez sur **Ajouter**.  
  
## Voir aussi  
 [Comment : ajouter des contrôles Bookmark à des documents Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Automatisation de Word à l'aide d'objets étendus](../vsto/automating-word-by-using-extended-objects.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Comment : redimensionner les contrôles NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Comment : redimensionner les contrôles ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  