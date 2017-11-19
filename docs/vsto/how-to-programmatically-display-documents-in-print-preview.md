---
title: "Comment : afficher des Documents par programmation dans l’aperçu avant impression | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], displaying documents in print preview
- documents [Office development in Visual Studio], displaying in print preview
ms.assetid: 96c7faea-9c5c-42b4-a009-08894a6d15c9
caps.latest.revision: "39"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 79facc7d8232a1dac5adc5f9e57848d4a206ba82
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-display-documents-in-print-preview"></a>Comment : afficher des documents en mode Aperçu avant impression par programmation
  Si votre solution génère un rapport, vous pouvez afficher ce dernier pour l’utilisateur en mode Aperçu avant impression.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="procedures-for-document-level-customizations"></a>Procédures pour les personnalisations au niveau du document  
  
#### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Pour afficher un document en mode Aperçu avant impression en appelant la méthode PrintPreview  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A> de la classe <xref:Microsoft.Office.Tools.Word.Document> . Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisDocument` de votre projet.  
  
     [!code-vb[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#13)]  
  
#### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Pour afficher un document en mode Aperçu avant impression en définissant la propriété PrintPreview  
  
1.  Affectez la valeur <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> à la propriété <xref:Microsoft.Office.Interop.Word.Application> de l'objet **true**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]  
  
## <a name="procedures-for-vsto-add-ins"></a>Procédures pour les compléments VSTO  
  
#### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Pour afficher un document en mode Aperçu avant impression en appelant la méthode PrintPreview  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A> du <xref:Microsoft.Office.Interop.Word.Document> dont vous souhaitez afficher l’aperçu. Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisAddIn` de votre projet.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#13)]  
  
#### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Pour afficher un document en mode Aperçu avant impression en définissant la propriété PrintPreview  
  
1.  Affectez la valeur <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> à la propriété <xref:Microsoft.Office.Interop.Word.Application> de l'objet **true**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : imprimer des Documents par programmation](../vsto/how-to-programmatically-print-documents.md)   
 [Comment : ouvrir des Documents existants par programmation](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Guide pratique pour créer des documents par programmation](../vsto/how-to-programmatically-create-new-documents.md)  
  
  