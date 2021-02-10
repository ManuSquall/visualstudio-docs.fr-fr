---
title: 'Comment : définir et sélectionner des plages dans les documents par programmation'
description: Découvrez comment vous pouvez définir et sélectionner des plages dans des documents Microsoft Word à l’aide de l’objet Range.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], selecting sentences
- documents [Office development in Visual Studio], ranges
- sentences, selecting in documents
- ranges, selecting in documents
- ranges, defining in documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e9c703f4d4e747934d1bab458b75a9d499f0d439
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963950"
---
# <a name="how-to-programmatically-define-and-select-ranges-in-documents"></a>Comment : définir et sélectionner des plages dans les documents par programmation
  Vous pouvez définir une plage dans un document Microsoft Office Word en utilisant un objet <xref:Microsoft.Office.Interop.Word.Range>. Vous pouvez sélectionner l’intégralité du document de plusieurs façons, par exemple, à l’aide <xref:Microsoft.Office.Interop.Word.Range.Select%2A> de la méthode de l' <xref:Microsoft.Office.Interop.Word.Range> objet, ou en utilisant la propriété de contenu de la <xref:Microsoft.Office.Tools.Word.Document> classe (dans une personnalisation au niveau du document) ou la <xref:Microsoft.Office.Interop.Word.Document> classe (dans un complément VSTO).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="define-a-range"></a>Définir une plage
 L'exemple suivant montre comment créer un objet <xref:Microsoft.Office.Interop.Word.Range> incluant les sept premiers caractères du document actif, y compris les caractères non imprimables. Puis, il sélectionne le texte dans la plage.

### <a name="to-define-a-range-in-a-document-level-customization"></a>Pour définir une plage dans une personnalisation au niveau du document

1. Ajoutez la plage au document en passant un caractère de début et de fin à la méthode <xref:Microsoft.Office.Tools.Word.Document.Range%2A> de la classe <xref:Microsoft.Office.Tools.Word.Document>. Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisDocument` de votre projet.

     [!code-vb[Trin_VstcoreWordAutomation#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#18)]
     [!code-csharp[Trin_VstcoreWordAutomation#18](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#18)]

### <a name="to-define-a-range-by-using-a-vsto-add-in"></a>Pour définir une plage en utilisant un complément VSTO

1. Ajoutez la plage au document en passant un caractère de début et de fin à la méthode <xref:Microsoft.Office.Interop.Word._Document.Range%2A> de la classe <xref:Microsoft.Office.Interop.Word.Document>. L'exemple de code suivant ajoute une plage au document actif. Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisAddIn` de votre projet.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#18)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#18](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#18)]

## <a name="select-a-range-in-a-document-level-customization"></a>Sélectionner une plage dans une personnalisation au niveau du document
 Les exemples suivants montrent comment sélectionner le document entier à l'aide de la méthode <xref:Microsoft.Office.Interop.Word.Range.Select%2A> d'un objet <xref:Microsoft.Office.Interop.Word.Range> ou de la propriété <xref:Microsoft.Office.Tools.Word.Document.Content%2A> de la classe <xref:Microsoft.Office.Tools.Word.Document>.

### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Pour sélectionner la totalité du document comme plage à l'aide de la méthode Select

1. Utilisez la méthode <xref:Microsoft.Office.Interop.Word.Range.Select%2A> d'un <xref:Microsoft.Office.Interop.Word.Range>qui contient la totalité du document. Pour utiliser l'exemple de code suivant, exécutez-le à partir de la classe `ThisDocument` de votre projet.

     [!code-vb[Trin_VstcoreWordAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#19)]
     [!code-csharp[Trin_VstcoreWordAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#19)]

### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>Pour sélectionner la totalité du document comme plage à l'aide de la propriété Content

1. Utilisez la propriété <xref:Microsoft.Office.Tools.Word.Document.Content%2A> pour définir une plage qui englobe la totalité du document.

    [!code-vb[Trin_VstcoreWordAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#20)]
    [!code-csharp[Trin_VstcoreWordAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#20)]

   Vous pouvez également utiliser les méthodes et les propriétés d'autres objets pour définir une plage.

### <a name="to-select-a-sentence-in-the-active-document"></a>Pour sélectionner une phrase dans le document actif

1. Définissez la plage à l'aide de la collection <xref:Microsoft.Office.Interop.Word.Sentences>. Utilisez l'index de la phrase que vous souhaitez sélectionner.

    [!code-vb[Trin_VstcoreWordAutomation#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#21)]
    [!code-csharp[Trin_VstcoreWordAutomation#21](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#21)]

   Une autre façon de sélectionner une phrase consiste à définir manuellement les valeurs de début et de fin de la plage.

### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>Pour sélectionner une phrase en définissant manuellement les valeurs de début et de fin

1. Créez une variable de plage.

     [!code-vb[Trin_VstcoreWordAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#23)]
     [!code-csharp[Trin_VstcoreWordAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#23)]

2. Vérifiez s’il existe au moins deux phrases dans le document, définissez les arguments de *début* et de *fin* de la plage, puis sélectionnez la plage.

     [!code-vb[Trin_VstcoreWordAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#24)]
     [!code-csharp[Trin_VstcoreWordAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#24)]

## <a name="select-a-range-by-using-a-vsto-add-in"></a>Sélectionner une plage à l’aide d’un complément VSTO
 Les exemples suivants montrent comment sélectionner le document entier à l'aide de la méthode <xref:Microsoft.Office.Interop.Word.Range.Select%2A> d'un objet <xref:Microsoft.Office.Interop.Word.Range> ou de la propriété <xref:Microsoft.Office.Interop.Word._Document.Content%2A> de la classe <xref:Microsoft.Office.Interop.Word.Document>.

### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Pour sélectionner la totalité du document comme plage à l'aide de la méthode Select

1. Utilisez la méthode <xref:Microsoft.Office.Interop.Word.Range.Select%2A> d'un <xref:Microsoft.Office.Interop.Word.Range>qui contient la totalité du document. L'exemple de code suivant sélectionne le contenu du document actif. Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisAddIn` de votre projet.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#19)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#19](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#19)]

### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>Pour sélectionner la totalité du document comme plage à l'aide de la propriété Content

1. Utilisez la propriété <xref:Microsoft.Office.Interop.Word._Document.Content%2A> pour définir une plage qui englobe la totalité du document.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#20)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#20](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#20)]

   Vous pouvez également utiliser les méthodes et les propriétés d'autres objets pour définir une plage.

### <a name="to-select-a-sentence-in-the-active-document"></a>Pour sélectionner une phrase dans le document actif

1. Définissez la plage à l'aide de la collection <xref:Microsoft.Office.Interop.Word.Sentences>. Utilisez l'index de la phrase que vous souhaitez sélectionner.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#21)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#21](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#21)]

   Une autre façon de sélectionner une phrase consiste à définir manuellement les valeurs de début et de fin de la plage.

### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>Pour sélectionner une phrase en définissant manuellement les valeurs de début et de fin

1. Créez une variable de plage.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#23)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#23](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#23)]

2. Vérifiez s’il existe au moins deux phrases dans le document, définissez les arguments de *début* et de *fin* de la plage, puis sélectionnez la plage.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#24)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#24](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#24)]

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble du modèle objet Word](../vsto/word-object-model-overview.md)
- [Comment : étendre des plages dans des documents par programmation](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Comment : récupérer des caractères de début et de fin dans les plages par programmation](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Comment : étendre des plages dans des documents par programmation](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Comment : réinitialiser des plages dans les documents Word par programmation](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Comment : réduire des plages ou des sélections dans des documents par programmation](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Comment : exclure des marques de paragraphe lors de la création de plages par programmation](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
