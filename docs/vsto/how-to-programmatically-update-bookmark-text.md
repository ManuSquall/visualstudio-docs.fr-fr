---
title: 'Comment : mettre à jour le texte d’un signet par programmation'
description: Découvrez comment vous pouvez utiliser Visual Studio pour insérer du texte par programmation dans un signet d’espace réservé dans un document Microsoft Word.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f67dbbe4d1d5c24d617f9cbc49a58ec2d134e90b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826198"
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

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet63":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet63":::

2. Assignez la chaîne *NewText* à la <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> propriété de <xref:Microsoft.Office.Tools.Word.Bookmark> .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet64":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet64":::

## <a name="use-word-objects"></a>Utiliser des objets Word

### <a name="to-update-bookmark-contents-using-a-word-bookmark-object"></a>Pour mettre à jour le contenu d'un signet à l'aide d'un objet Bookmark Word

1. Créez une procédure qui accepte un argument `bookmark` comme nom du <xref:Microsoft.Office.Interop.Word.Bookmark> et un argument `newText` comme chaîne à attribuer à la propriété <xref:Microsoft.Office.Interop.Word.Range.Text%2A> du signet.

    > [!NOTE]
    > L'assignation de texte à un objet Word <xref:Microsoft.Office.Interop.Word.Bookmark> natif entraîne la suppression du signet.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet65":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet65":::

2. Assignez la chaîne *NewText* à la <xref:Microsoft.Office.Interop.Word.Range.Text%2A> propriété du signet, qui supprime automatiquement le signet. Puis, ajoutez de nouveau le signet à la collection <xref:Microsoft.Office.Interop.Word.Bookmarks>.

     L'exemple de code suivant peut être utilisé dans une personnalisation au niveau du document.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet66":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet66":::

     L'exemple de code suivant peut être utilisé dans un complément VSTO. Cet exemple utilise le document actif.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet66":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet66":::

## <a name="see-also"></a>Voir aussi
- [Comment : insérer du texte dans des documents Word par programmation](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Vue d’ensemble du modèle objet Word](../vsto/word-object-model-overview.md)
- [Bookmark, contrôle](../vsto/bookmark-control.md)
