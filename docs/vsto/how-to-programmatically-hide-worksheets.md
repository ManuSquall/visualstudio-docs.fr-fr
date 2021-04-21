---
title: 'Comment : masquer des feuilles de calcul par programmation'
description: Découvrez comment vous pouvez afficher ou masquer une feuille de calcul dans un classeur Microsoft Excel à l’aide de l’élément hôte de feuille de calcul.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden worksheets
- worksheets, hiding
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b859ea468db86d57347553f9fd10b44fea99026b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826471"
---
# <a name="how-to-programmatically-hide-worksheets"></a>Comment : masquer des feuilles de calcul par programmation
  Vous pouvez afficher ou masquer une feuille de calcul dans un classeur. Pour masquer une feuille de calcul, utilisez l’élément hôte de feuille de calcul ou accédez à la feuille de calcul à l’aide de la collection Sheets du classeur.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-the-worksheet-host-item"></a>Utiliser l’élément hôte de feuille de calcul
 Si la feuille de calcul a été ajoutée au moment du design dans une personnalisation au niveau du document, utilisez la propriété <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> pour masquer la feuille de calcul spécifiée.

### <a name="to-hide-a-worksheet-using-a-worksheet-host-item"></a>Pour masquer une feuille de calcul à l’aide d’un élément hôte de feuille de calcul

1. Affectez à la propriété <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> de l’élément hôte `Sheet1` la valeur d’énumération <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet25":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet25":::

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Utiliser la collection Sheets du classeur Excel
 Accédez aux feuilles de calcul via la collection <xref:Microsoft.Office.Interop.Excel.Sheets> Microsoft Office Excel dans les cas suivants :

- Vous souhaitez masquer une feuille de calcul dans un complément VSTO.

- La feuille de calcul à masquer a été créée au moment de l’exécution dans une personnalisation au niveau du document.

### <a name="to-hide-a-worksheet-using-the-sheets-collection-of-the-excel-workbook"></a>Pour masquer une feuille de calcul à l’aide de la collection Sheets du classeur Excel

1. Affectez à la propriété <xref:Microsoft.Office.Interop.Excel.Worksheets.Visible%2A> de la feuille de calcul la valeur d’énumération <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet26":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet26":::

## <a name="see-also"></a>Voir aussi
- [Utiliser des feuilles de calcul](../vsto/working-with-worksheets.md)
- [Comment : supprimer des feuilles de calcul à partir de classeurs par programmation](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Comment : déplacer des feuilles de calcul dans des classeurs par programmation](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)
- [Comment : protéger des feuilles de calcul par programmation](../vsto/how-to-programmatically-protect-worksheets.md)
- [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
- [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)
