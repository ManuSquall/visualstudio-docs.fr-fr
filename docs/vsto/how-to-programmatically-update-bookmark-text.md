---
title: 'Comment : mettre à jour le texte d’un signet par programmation'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, updating text
- text [Office development in Visual Studio], updating in bookmarks
- Bookmark control, updating contents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9b76c239606a4bf0d6da203bd4eea45a11162706
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546950"
---
# <a name="how-to-programmatically-update-bookmark-text"></a>Comment : mettre à jour le texte d’un signet par programmation
  Vous pouvez insérer un texte dans un signet d'espace réservé d'un document Microsoft Office Word afin de pouvoir récupérer le texte ultérieurement, ou pour remplacer le texte d'un signet. Si vous développez une personnalisation au niveau du document, vous pouvez également mettre à jour le texte dans un contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> lié aux données. Pour plus d’informations, consultez [lier des données à des contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 L'objet Bookmark peut être de deux types :

- Un contrôle hôte <xref:Microsoft.Office.Tools.Word.Bookmark>.

   Les contrôles <xref:Microsoft.Office.Tools.Word.Bookmark> étendent les objets <xref:Microsoft.Office.Interop.Word.Bookmark> natifs en activant la liaison de données et en exposant les événements. Pour plus d’informations sur les contrôles hôtes, consultez [vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md).

- Objet <xref:Microsoft.Office.Interop.Word.Bookmark> natif.

   Les objets <xref:Microsoft.Office.Interop.Word.Bookmark> n'ont pas de fonctionnalités de liaison de données ou d'événements.

  Lorsque vous assignez un texte à un signet, le comportement diffère entre un <xref:Microsoft.Office.Interop.Word.Bookmark> et un <xref:Microsoft.Office.Tools.Word.Bookmark>. Pour plus d’informations, consultez [contrôle Bookmark](../vsto/bookmark-control.md).

## <a name="use-host-controls"></a>Utiliser des contrôles hôtes

### <a name="to-update-bookmark-contents-using-a-bookmark-control"></a>Pour mettre à jour le contenu d'un signet à l'aide d'un contrôle Bookmark

1. Créez une procédure qui accepte un argument `bookmark` comme nom du signet et un argument `newText` comme chaîne à attribuer à la propriété <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A>.

    > [!NOTE]
    > L'affectation de texte à la propriété <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> ou <xref:Microsoft.Office.Tools.Word.Bookmark.FormattedText%2A> d'un contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> n'entraîne pas la suppression du signet.

     [!code-vb[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#63)]
     [!code-csharp[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#63)]

2. Assignez la chaîne *NewText* à la <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> propriété de <xref:Microsoft.Office.Tools.Word.Bookmark> .

     [!code-vb[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#64)]
     [!code-csharp[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#64)]

## <a name="use-word-objects"></a>Utiliser des objets Word

### <a name="to-update-bookmark-contents-using-a-word-bookmark-object"></a>Pour mettre à jour le contenu d'un signet à l'aide d'un objet Bookmark Word

1. Créez une procédure qui accepte un argument `bookmark` comme nom du <xref:Microsoft.Office.Interop.Word.Bookmark> et un argument `newText` comme chaîne à attribuer à la propriété <xref:Microsoft.Office.Interop.Word.Range.Text%2A> du signet.

    > [!NOTE]
    > L'assignation de texte à un objet Word <xref:Microsoft.Office.Interop.Word.Bookmark> natif entraîne la suppression du signet.

     [!code-vb[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#65)]
     [!code-csharp[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#65)]

2. Assignez la chaîne *NewText* à la <xref:Microsoft.Office.Interop.Word.Range.Text%2A> propriété du signet, qui supprime automatiquement le signet. Puis, ajoutez de nouveau le signet à la collection <xref:Microsoft.Office.Interop.Word.Bookmarks>.

     L'exemple de code suivant peut être utilisé dans une personnalisation au niveau du document.

     [!code-vb[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#66)]

     L'exemple de code suivant peut être utilisé dans un complément VSTO. Cet exemple utilise le document actif.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#66)]

## <a name="see-also"></a>Voir aussi
- [Comment : insérer du texte dans des documents Word par programmation](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Vue d’ensemble du modèle objet Word](../vsto/word-object-model-overview.md)
- [Bookmark, contrôle](../vsto/bookmark-control.md)
