---
title: 'Comment : imprimer des feuilles de calcul par programmation | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- worksheets, printing
- print preview, worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9d9bd4d28afb1eca2ff07a8847081864c7af5744
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-print-worksheets"></a>Comment : imprimer des feuilles de calcul par programmation
  Vous pouvez imprimer une feuille de calcul dans un classeur.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="printing-a-worksheet-in-a-document-level-customization"></a>Impression d'une feuille de calcul dans une personnalisation au niveau du document  
  
#### <a name="to-print-a-worksheet"></a>Pour imprimer une feuille de calcul  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintOut%2A> de `Sheet1`, demandez deux exemplaires et prévisualisez le document avant l'impression.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#22)]
     [!code-vb[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#22)]  
  
 Le <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> méthode vous permet d’afficher l’objet spécifié dans le **Aperçu avant impression** fenêtre. Le code suivant suppose que vous ayez un élément hôte <xref:Microsoft.Office.Tools.Excel.Worksheet> nommé `Sheet1`.  
  
#### <a name="to-preview-a-page-before-printing"></a>Pour afficher une page avant l'impression  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> de la feuille de calcul.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#23)]  
  
## <a name="printing-a-worksheet-in-a-vsto-add-in"></a>Impression d’une feuille de calcul dans un complément VSTO  
  
#### <a name="to-print-a-worksheet"></a>Pour imprimer une feuille de calcul  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A> de la feuille de calcul active, demandez deux exemplaires et prévisualisez le document avant l'impression.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#14)]  
  
 Le <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> méthode vous permet d’afficher l’objet spécifié dans le **Aperçu avant impression** fenêtre.  
  
#### <a name="to-preview-a-page-before-printing"></a>Pour afficher une page avant l'impression  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> de la feuille de calcul active.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#15)]  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des feuilles de calcul](../vsto/working-with-worksheets.md)   
 [Comment : vérifier l’orthographe dans les feuilles de calcul par programmation](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [Élément hôte de feuille de calcul](../vsto/worksheet-host-item.md)   
 [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  