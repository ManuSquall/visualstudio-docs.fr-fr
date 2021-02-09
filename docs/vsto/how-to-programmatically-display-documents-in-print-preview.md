---
title: 'Comment : afficher des documents en mode aperçu avant impression par programmation'
description: Découvrez comment vous pouvez afficher des documents en mode aperçu avant impression dans un document Microsoft Word.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], displaying documents in print preview
- documents [Office development in Visual Studio], displaying in print preview
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 14005f465fd4394e86450017530de457a97b3d4f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885545"
---
# <a name="how-to-programmatically-display-documents-in-print-preview"></a>Comment : afficher des documents en mode aperçu avant impression par programmation
  Si votre solution génère un rapport, vous pouvez afficher ce dernier pour l’utilisateur en mode Aperçu avant impression.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="procedures-for-document-level-customizations"></a>Procédures pour les personnalisations au niveau du document

### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Pour afficher un document en mode Aperçu avant impression en appelant la méthode PrintPreview

1. Appelez la méthode <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A> de la classe <xref:Microsoft.Office.Tools.Word.Document> . Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisDocument` de votre projet.

     [!code-vb[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#13)]

### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Pour afficher un document en mode Aperçu avant impression en définissant la propriété PrintPreview

1. Affectez la valeur <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> à la propriété <xref:Microsoft.Office.Interop.Word.Application> de l'objet **true**.

     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]

## <a name="procedures-for-vsto-add-ins"></a>Procédures pour les compléments VSTO

### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Pour afficher un document en mode Aperçu avant impression en appelant la méthode PrintPreview

1. Appelez la méthode <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A> du <xref:Microsoft.Office.Interop.Word.Document> dont vous souhaitez afficher l’aperçu. Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisAddIn` de votre projet.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#13)]

### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Pour afficher un document en mode Aperçu avant impression en définissant la propriété PrintPreview

1. Affectez la valeur <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> à la propriété <xref:Microsoft.Office.Interop.Word.Application> de l'objet **true**.

     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]

## <a name="see-also"></a>Voir aussi
- [Comment : imprimer des documents par programmation](../vsto/how-to-programmatically-print-documents.md)
- [Comment : ouvrir des documents existants par programmation](../vsto/how-to-programmatically-open-existing-documents.md)
- [Comment : créer des documents par programmation](../vsto/how-to-programmatically-create-new-documents.md)
