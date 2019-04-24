---
title: 'Procédure : Mettre à jour par programme de texte d’un signet'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 12a64f35e7d530b80e44f3098035093509766c60
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60113025"
---
# <a name="how-to-programmatically-update-bookmark-text"></a>Procédure : Mettre à jour par programme de texte d’un signet
  Vous pouvez insérer un texte dans un signet d'espace réservé d'un document Microsoft Office Word afin de pouvoir récupérer le texte ultérieurement, ou pour remplacer le texte d'un signet. Si vous développez une personnalisation au niveau du document, vous pouvez également mettre à jour le texte dans un contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> lié aux données. Pour plus d’informations, consultez [lier des données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 L'objet Bookmark peut être de deux types :

- Un contrôle hôte <xref:Microsoft.Office.Tools.Word.Bookmark>.

   Les contrôles <xref:Microsoft.Office.Tools.Word.Bookmark> étendent les objets <xref:Microsoft.Office.Interop.Word.Bookmark> natifs en activant la liaison de données et en exposant les événements. Pour plus d’informations sur les contrôles hôtes, consultez [éléments hôtes et héberger de vue d’ensemble des contrôles](../vsto/host-items-and-host-controls-overview.md).

- Un objet <xref:Microsoft.Office.Interop.Word.Bookmark> natif.

   Les objets <xref:Microsoft.Office.Interop.Word.Bookmark> n'ont pas de fonctionnalités de liaison de données ou d'événements.

  Lorsque vous assignez un texte à un signet, le comportement diffère entre un <xref:Microsoft.Office.Interop.Word.Bookmark> et un <xref:Microsoft.Office.Tools.Word.Bookmark>. Pour plus d’informations, consultez [Bookmark (contrôle)](../vsto/bookmark-control.md).

## <a name="use-host-controls"></a>Utiliser les contrôles hôtes

### <a name="to-update-bookmark-contents-using-a-bookmark-control"></a>Pour mettre à jour le contenu d'un signet à l'aide d'un contrôle Bookmark

1. Créez une procédure qui accepte un argument `bookmark` comme nom du signet et un argument `newText` comme chaîne à attribuer à la propriété <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A>.

    > [!NOTE]
    >  L'affectation de texte à la propriété <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> ou <xref:Microsoft.Office.Tools.Word.Bookmark.FormattedText%2A> d'un contrôle <xref:Microsoft.Office.Tools.Word.Bookmark> n'entraîne pas la suppression du signet.

     [!code-vb[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#63)]
     [!code-csharp[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#63)]

2. Affecter le *newText* de chaîne pour le <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> propriété de la <xref:Microsoft.Office.Tools.Word.Bookmark>.

     [!code-vb[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#64)]
     [!code-csharp[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#64)]

## <a name="use-word-objects"></a>Utiliser des objets Word

### <a name="to-update-bookmark-contents-using-a-word-bookmark-object"></a>Pour mettre à jour le contenu d'un signet à l'aide d'un objet Bookmark Word

1. Créez une procédure qui accepte un argument `bookmark` comme nom du <xref:Microsoft.Office.Interop.Word.Bookmark> et un argument `newText` comme chaîne à attribuer à la propriété <xref:Microsoft.Office.Interop.Word.Range.Text%2A> du signet.

    > [!NOTE]
    >  L'assignation de texte à un objet Word <xref:Microsoft.Office.Interop.Word.Bookmark> natif entraîne la suppression du signet.

     [!code-vb[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#65)]
     [!code-csharp[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#65)]

2. Affecter le *newText* de chaîne pour le <xref:Microsoft.Office.Interop.Word.Range.Text%2A> propriété du signet, ce qui supprime automatiquement le signet. Puis, ajoutez de nouveau le signet à la collection <xref:Microsoft.Office.Interop.Word.Bookmarks>.

     Vous pouvez utiliser l’exemple de code suivant dans une personnalisation au niveau du document.

     [!code-vb[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#66)]

     L'exemple de code suivant peut être utilisé dans un complément VSTO. Cet exemple utilise le document actif.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#66)]

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour Insérer du texte dans les documents Word par programmation](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Vue d’ensemble du modèle d’objet Word](../vsto/word-object-model-overview.md)
- [Bookmark (contrôle)](../vsto/bookmark-control.md)
