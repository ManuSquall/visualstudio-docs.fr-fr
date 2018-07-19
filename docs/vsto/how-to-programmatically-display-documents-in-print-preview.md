---
title: 'Comment : afficher des documents par programmation dans l’aperçu avant impression'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], displaying documents in print preview
- documents [Office development in Visual Studio], displaying in print preview
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1a2ab538707156826be3a31252cde16e67edff9c
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257223"
---
# <a name="how-to-programmatically-display-documents-in-print-preview"></a>Comment : afficher des documents par programmation dans l’aperçu avant impression
  Si votre solution génère un rapport, vous pouvez afficher ce dernier pour l’utilisateur en mode Aperçu avant impression.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="procedures-for-document-level-customizations"></a>Procédures pour les personnalisations au niveau du document  
  
### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Pour afficher un document en mode Aperçu avant impression en appelant la méthode PrintPreview  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A> de la classe <xref:Microsoft.Office.Tools.Word.Document> . Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisDocument` de votre projet.  
  
     [!code-vb[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#13)]  
  
### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Pour afficher un document en mode Aperçu avant impression en définissant la propriété PrintPreview  
  
1.  Affectez la valeur <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> à la propriété <xref:Microsoft.Office.Interop.Word.Application> de l'objet **true**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]  
  
## <a name="procedures-for-vsto-add-ins"></a>Procédures pour les compléments VSTO  
  
### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Pour afficher un document en mode Aperçu avant impression en appelant la méthode PrintPreview  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A> du <xref:Microsoft.Office.Interop.Word.Document> dont vous souhaitez afficher l’aperçu. Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisAddIn` de votre projet.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#13)]  
  
### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Pour afficher un document en mode Aperçu avant impression en définissant la propriété PrintPreview  
  
1.  Affectez la valeur <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> à la propriété <xref:Microsoft.Office.Interop.Word.Application> de l'objet **true**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : imprimer des documents par programmation](../vsto/how-to-programmatically-print-documents.md)   
 [Comment : ouvrir des documents existants par programmation](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Comment : créer par programme des documents](../vsto/how-to-programmatically-create-new-documents.md)  
  
  