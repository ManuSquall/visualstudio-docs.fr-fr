---
title: 'Comment : imprimer des feuilles de calcul par programmation'
description: Découvrez comment vous pouvez utiliser Visual Studio pour imprimer par programmation une feuille de calcul dans un classeur Microsoft Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- worksheets, printing
- print preview, worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 129493f726967776aa669eb92f6e912ed9c1b11b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827147"
---
# <a name="how-to-programmatically-print-worksheets"></a>Comment : imprimer des feuilles de calcul par programmation

Vous pouvez imprimer une feuille de calcul dans un classeur.

[!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="print-a-worksheet-in-a-document-level-customization"></a>Imprimer une feuille de calcul dans une personnalisation au niveau du document

### <a name="to-print-a-worksheet"></a>Pour imprimer une feuille de calcul

1. Appelez la méthode `PrintOut` de `Sheet1`, demandez deux exemplaires et prévisualisez le document avant l'impression.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet22":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet22":::

   La <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> méthode vous permet d’afficher l’objet spécifié dans la fenêtre d' **Aperçu avant impression** . Le code suivant suppose que vous ayez un élément hôte <xref:Microsoft.Office.Tools.Excel.Worksheet> nommé `Sheet1`.

### <a name="to-preview-a-page-before-printing"></a>Pour afficher une page avant l'impression

1. Appelez la méthode <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> de la feuille de calcul.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet23":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet23":::

## <a name="print-a-worksheet-in-a-vsto-add-in"></a>Imprimer une feuille de calcul dans un complément VSTO

### <a name="to-print-a-worksheet"></a>Pour imprimer une feuille de calcul

1. Appelez la méthode <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A> de la feuille de calcul active, demandez deux exemplaires et prévisualisez le document avant l'impression.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet14":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet14":::

   La <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> méthode vous permet d’afficher l’objet spécifié dans la fenêtre d' **Aperçu avant impression** .

### <a name="to-preview-a-page-before-printing"></a>Pour afficher une page avant l'impression

1. Appelez la méthode <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> de la feuille de calcul active.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet15":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet15":::

## <a name="see-also"></a>Voir aussi

- [Utiliser des feuilles de calcul](../vsto/working-with-worksheets.md)
- [Comment : vérifier l’orthographe dans les feuilles de calcul par programmation](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [Élément hôte de feuille de calcul](../vsto/worksheet-host-item.md)
- [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
