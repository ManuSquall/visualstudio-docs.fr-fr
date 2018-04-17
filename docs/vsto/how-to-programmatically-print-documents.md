---
title: 'Comment : imprimer des Documents par programmation | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], printing documents
- documents [Office development in Visual Studio], printing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1a5364bd2cf0f0ea6d5e7ceb7c8a427c5aea301d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-print-documents"></a>Comment : imprimer des documents par programmation
  Vous pouvez imprimer tout un document Microsoft Office Word, ou seulement une partie, vers votre imprimante par défaut.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="printing-a-document-that-is-part-of-a-document-level-customization"></a>Impression d’un document qui fait partie d’une personnalisation au niveau du document  
  
#### <a name="to-print-the-entire-document"></a>Pour imprimer tout le document  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> de la classe `ThisDocument` dans votre projet pour imprimer tout le document. Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisDocument` .  
  
     [!code-vb[Trin_VstcoreWordAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#11)]
     [!code-csharp[Trin_VstcoreWordAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#11)]  
  
#### <a name="to-print-the-current-page-of-the-document"></a>Pour imprimer la page active du document  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> de la classe `ThisDocument` dans votre projet et spécifiez l’impression d’une seule copie de la page active. Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisDocument` .  
  
     [!code-vb[Trin_VstcoreWordAutomation#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#12)]
     [!code-csharp[Trin_VstcoreWordAutomation#12](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#12)]  
  
## <a name="printing-a-document-by-using-an-vsto-add-in"></a>Impression d’un document à l’aide d’un complément VSTO  
  
#### <a name="to-print-an-entire-document"></a>Pour imprimer tout un document  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> de l’objet <xref:Microsoft.Office.Interop.Word.Document> à imprimer. L’exemple de code suivant imprime le document actif. Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisAddIn` dans votre projet.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#11)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#11](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#11)]  
  
#### <a name="to-print-the-current-page-of-a-document"></a>Pour imprimer la page active d’un document  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> de l’objet <xref:Microsoft.Office.Interop.Word.Document> à imprimer, puis spécifiez l’impression d’une seule copie de la page active. L’exemple de code suivant imprime le document actif. Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisAddIn` dans votre projet.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#12)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#12](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#12)]  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  