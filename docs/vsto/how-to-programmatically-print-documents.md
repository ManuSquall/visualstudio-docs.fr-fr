---
title: "Comment : imprimer des Documents par programmation | Documents Microsoft"
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
- Word [Office development in Visual Studio], printing documents
- documents [Office development in Visual Studio], printing
ms.assetid: 99285d98-1bb7-4ccb-83d9-e917b0a9ea42
caps.latest.revision: "53"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: ec4808adeb38d0ee8cf13d28e181260fbbae95bc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
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
  
  