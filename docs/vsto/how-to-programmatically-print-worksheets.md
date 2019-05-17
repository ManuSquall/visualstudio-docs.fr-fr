---
title: 'Procédure : Imprimer des feuilles de calcul par programmation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- worksheets, printing
- print preview, worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 76315f6cde5bc54385e217a8f234389a7f45e621
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955922"
---
# <a name="how-to-programmatically-print-worksheets"></a>Procédure : Imprimer des feuilles de calcul par programmation
  Vous pouvez imprimer une feuille de calcul dans un classeur.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="print-a-worksheet-in-a-document-level-customization"></a>Imprimer une feuille de calcul dans une personnalisation au niveau du document

### <a name="to-print-a-worksheet"></a>Pour imprimer une feuille de calcul

1. Appelez la méthode <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintOut%2A> de `Sheet1`, demandez deux exemplaires et prévisualisez le document avant l'impression.

    [!code-csharp[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#22)]
    [!code-vb[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#22)]

   Le <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> méthode vous permet d’afficher l’objet spécifié dans le **Aperçu avant impression** fenêtre. Le code suivant suppose que vous ayez un élément hôte <xref:Microsoft.Office.Tools.Excel.Worksheet> nommé `Sheet1`.

### <a name="to-preview-a-page-before-printing"></a>Pour afficher une page avant l'impression

1. Appelez la méthode <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> de la feuille de calcul.

     [!code-csharp[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#23)]

## <a name="print-a-worksheet-in-a-vsto-add-in"></a>Imprimer une feuille de calcul dans un composant logiciel complément VSTO

### <a name="to-print-a-worksheet"></a>Pour imprimer une feuille de calcul

1. Appelez la méthode <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A> de la feuille de calcul active, demandez deux exemplaires et prévisualisez le document avant l'impression.

    [!code-csharp[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#14)]
    [!code-vb[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#14)]

   Le <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> méthode vous permet d’afficher l’objet spécifié dans le **Aperçu avant impression** fenêtre.

### <a name="to-preview-a-page-before-printing"></a>Pour afficher une page avant l'impression

1. Appelez la méthode <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> de la feuille de calcul active.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#15)]

## <a name="see-also"></a>Voir aussi
- [Travailler avec des feuilles de calcul](../vsto/working-with-worksheets.md)
- [Guide pratique pour Vérifier l’orthographe dans les feuilles de calcul par programmation](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [Élément hôte de feuille de calcul](../vsto/worksheet-host-item.md)
- [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
