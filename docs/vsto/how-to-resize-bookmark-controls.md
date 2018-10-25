---
title: 'Comment : redimensionner les contrôles Bookmark'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- Bookmark control, resizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 57b6d6a089570c52607cf73eeed4fc00978ab251
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49924835"
---
# <a name="how-to-resize-bookmark-controls"></a>Comment : redimensionner les contrôles Bookmark
  Vous définissez la taille d’un contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> quand vous l’ajoutez à un document Microsoft Office Word. Vous pouvez également le redimensionner ultérieurement.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Il existe trois manières de redimensionner un signet :  
  
- Ajouter ou supprimer du texte dans le contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> .  
  
   Quand vous ajoutez du texte dans un signet, la taille du signet augmente automatiquement pour contenir le nouveau texte. Quand vous supprimez du texte, la taille du signet diminue automatiquement.  
  
- Modifier les propriétés <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> et <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> du contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> .  
  
   C’est utile si vous ne modifiez la taille que de quelques caractères.  
  
- Recréer le contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> .  
  
   C’est utile en cas de modification substantielle de la taille ou de l’emplacement d’un signet.  
  
  Dans les projets au niveau du document, vous pouvez ajouter des contrôles <xref:Microsoft.Office.Tools.Word.Bookmark> au document de votre projet au moment du design ou au moment de l'exécution. Dans les projets de complément VSTO, vous pouvez ajouter <xref:Microsoft.Office.Tools.Word.Bookmark> contrôles à tout document ouvert au moment de l’exécution. Pour plus d’informations, consultez [Comment : ajouter un signet de contrôles à des documents Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md).  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="change-the-start-and-end-properties"></a>Modifier les propriétés de début et de fin  
  
### <a name="to-resize-a-bookmark-in-a-document-level-project-at-design-time"></a>Pour redimensionner un signet dans un projet au niveau du document au moment du design  
  
1.  Sélectionnez le signet dans la fenêtre **Propriétés** .  
  
2.  Augmentez ou diminuez la valeur de la propriété <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> .  
  
3.  Augmentez ou diminuez la valeur de la propriété <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> .  
  
### <a name="to-resize-a-bookmark-in-a-document-level-project-at-runtime"></a>Pour redimensionner un signet dans un projet au niveau du document lors de l’exécution  
  
1.  Modifier le <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> et <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> propriétés d’un <xref:Microsoft.Office.Tools.Word.Bookmark> vous avez créé lors de l’exécution ou au moment du design.  
  
     L’exemple de code suivant ajoute cinq caractères au début d’un signet nommé `SampleBookmark`. Ce code part du principe qu’il existe au moins cinq caractères de texte avant le signet.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#2](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#2)]  
  
     L’exemple de code suivant ajoute cinq caractères à la fin du même signet. Ce code part du principe qu’il existe au moins cinq caractères de texte après le signet.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#3](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#3)]  
  
### <a name="to-resize-a-bookmark-in-a-vsto-add-in-project-at-runtime"></a>Pour redimensionner un signet dans un projet de complément VSTO lors de l’exécution  
  
1.  Modifier le <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> et <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> propriétés d’un <xref:Microsoft.Office.Tools.Word.Bookmark> que vous avez créé lors de l’exécution.  
  
     L’exemple de code suivant crée un <xref:Microsoft.Office.Tools.Word.Bookmark> qui contient le texte du premier paragraphe du document actif, puis il supprime cinq caractères au début et à la fin du <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     [!code-vb[Trin_WordAddInDynamicControls#16](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#16)]
     [!code-csharp[Trin_WordAddInDynamicControls#16](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#16)]  
  
## <a name="recreate-the-bookmark"></a>Recréer le signet  
 Vous pouvez redimensionner un signet dans un projet au niveau du document en ajoutant un nouveau signet du même nom que le signet existant, mais avec une taille différente.  
  
### <a name="to-recreate-a-bookmark-in-a-document-level-project-at-design-time"></a>Pour recréer un signet dans un projet au niveau du document au moment du design  
  
1.  Sélectionnez le texte à inclure dans le nouveau contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> .  
  
2.  Dans le menu **Insérer** , cliquez sur **Signet**.  
  
3.  Dans la boîte de dialogue **Signet** , sélectionnez le nom du signet à redimensionner et cliquez sur **Ajouter**.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : ajouter des contrôles Bookmark à des documents Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Automatiser Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md)   
 [Éléments hôtes et la vue d’ensemble des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Comment : redimensionner les contrôles NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Comment : redimensionner les contrôles ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Limitations de programmation des éléments hôtes et contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  