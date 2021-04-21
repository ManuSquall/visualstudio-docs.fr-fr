---
title: 'Comment : imprimer des documents par programmation'
description: Découvrez comment vous pouvez imprimer un document Microsoft Word entier, ou une partie d’un document, sur votre imprimante par défaut.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], printing documents
- documents [Office development in Visual Studio], printing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 47f295a6259b8d722c9c3c714b62fe648bdea1c6
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827199"
---
# <a name="how-to-programmatically-print-documents"></a>Comment : imprimer des documents par programmation
  Vous pouvez imprimer tout un document Microsoft Office Word, ou seulement une partie, vers votre imprimante par défaut.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="print-a-document-that-is-part-of-a-document-level-customization"></a>Imprimer un document qui fait partie d’une personnalisation au niveau du document

### <a name="to-print-the-entire-document"></a>Pour imprimer tout le document

1. Appelez la méthode <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> de la classe `ThisDocument` dans votre projet pour imprimer tout le document. Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisDocument` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet11":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet11":::

### <a name="to-print-the-current-page-of-the-document"></a>Pour imprimer la page active du document

1. Appelez la méthode <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> de la classe `ThisDocument` dans votre projet et spécifiez l’impression d’une seule copie de la page active. Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisDocument` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet12":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet12":::

## <a name="print-a-document-by-using-a-vsto-add-in"></a>Imprimer un document à l’aide d’un complément VSTO

### <a name="to-print-an-entire-document"></a>Pour imprimer tout un document

1. Appelez la méthode <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> de l’objet <xref:Microsoft.Office.Interop.Word.Document> à imprimer. L’exemple de code suivant imprime le document actif. Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisAddIn` dans votre projet.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet11":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet11":::

### <a name="to-print-the-current-page-of-a-document"></a>Pour imprimer la page active d’un document

1. Appelez la méthode <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> de l’objet <xref:Microsoft.Office.Interop.Word.Document> à imprimer, puis spécifiez l’impression d’une seule copie de la page active. L’exemple de code suivant imprime le document actif. Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisAddIn` dans votre projet.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet12":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet12":::

## <a name="see-also"></a>Voir aussi
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
