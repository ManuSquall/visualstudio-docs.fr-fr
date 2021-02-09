---
title: 'Comment : ajouter des feuilles de calcul à des classeurs par programmation'
description: Découvrez comment vous pouvez créer par programmation une feuille de calcul, puis ajouter la feuille de calcul à la collection de feuilles de calcul dans le classeur.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, adding worksheets
- workbooks, creating worksheets
- worksheets, creating
- worksheets, adding to workbooks
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: babf029550907cb7faef77b71bdfae25a1307f38
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879460"
---
# <a name="how-to-programmatically-add-new-worksheets-to-workbooks"></a>Comment : ajouter des feuilles de calcul à des classeurs par programmation
  Vous pouvez créer par programmation une feuille de calcul, puis ajouter la feuille de calcul à la collection de feuilles de calcul du classeur.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-add-a-new-worksheet-to-a-workbook-in-a-document-level-customization"></a>Pour ajouter une nouvelle feuille de calcul à un classeur dans une personnalisation au niveau du document

1. Utilisez la méthode <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> de la collection <xref:Microsoft.Office.Interop.Excel.Sheets> .

     [!code-csharp[Trin_VstcoreExcelAutomation#15](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomation#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#15)]

     La nouvelle feuille de calcul est un objet <xref:Microsoft.Office.Interop.Excel.Worksheet> natif et non un élément hôte. Si vous souhaitez ajouter un élément hôte <xref:Microsoft.Office.Tools.Excel.Worksheet> , vous devez ajouter la feuille de calcul au moment du design.

## <a name="to-add-a-new-worksheet-to-a-workbook-in-a-vsto-add-in"></a>Pour ajouter une nouvelle feuille de calcul à un classeur dans un complément VSTO

1. Utilisez la méthode <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> de la collection <xref:Microsoft.Office.Interop.Excel.Sheets> .

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#11)]

     La nouvelle feuille de calcul est un objet <xref:Microsoft.Office.Interop.Excel.Worksheet> natif et non un élément hôte. Vous pouvez également générer un élément hôte <xref:Microsoft.Office.Tools.Excel.Worksheet> à partir de l'objet <xref:Microsoft.Office.Interop.Excel.Worksheet> natif. Pour plus d'informations, consultez [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>Voir aussi
- [Utiliser des feuilles de calcul](../vsto/working-with-worksheets.md)
- [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
- [Comment : supprimer des feuilles de calcul à partir de classeurs par programmation](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Comment : sélectionner des feuilles de calcul par programmation](../vsto/how-to-programmatically-select-worksheets.md)
- [Automatiser Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)
- [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
