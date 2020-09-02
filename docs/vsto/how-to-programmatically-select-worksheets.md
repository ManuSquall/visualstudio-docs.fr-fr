---
title: 'Comment : sélectionner des feuilles de calcul par programmation'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, selecting
- Excel projects, selecting worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6134b23e7b398794529ee43a428ee8b8962ccf38
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547002"
---
# <a name="how-to-programmatically-select-worksheets"></a>Comment : sélectionner des feuilles de calcul par programmation
  La méthode <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> méthode sélectionne l'objet spécifié, ce qui déplace la sélection de l'utilisateur vers le nouvel objet. Utilisez la méthode <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A> si vous souhaitez donner le focus à l'objet sans modifier la sélection de l'utilisateur.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Si vous souhaitez sélectionner une feuille de calcul existante dans un complément VSTO ou si la feuille de calcul a été créée au moment de l’exécution dans une personnalisation au niveau du document, vous devez y accéder à l’aide <xref:Microsoft.Office.Interop.Excel.Sheets> de la collection Excel du classeur Excel ; dans le cas contraire, vous pouvez accéder directement à l' <xref:Microsoft.Office.Tools.Excel.Worksheet> élément hôte.

## <a name="use-the-worksheet-host-item"></a>Utiliser l’élément hôte de feuille de calcul
 Dans une personnalisation au niveau du document, ajoutez le code suivant à *Feuil1. vb* ou *Sheet1.cs*.

### <a name="to-select-the-first-worksheet-in-a-workbook-using-a-host-item"></a>Pour sélectionner la première feuille de calcul d'un classeur à l'aide d'un élément hôte

1. Appelez la méthode <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> de `Sheet1`.

     [!code-csharp[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#19)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Utiliser la collection Sheets du classeur Excel
 Accédez à la feuille de calcul en utilisant la collection Excel <xref:Microsoft.Office.Interop.Excel.Sheets>.

### <a name="to-select-the-first-worksheet-in-a-workbook-using-the-sheets-collection-of-the-excel-workbook"></a>Pour sélectionner la première feuille de calcul d'un classeur en utilisant la collection Sheets du classeur Excel

1. Appelez la méthode <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> de la collection <xref:Microsoft.Office.Interop.Excel.Sheets> pour sélectionner la première feuille de calcul du classeur actif.

     [!code-csharp[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#20)]

## <a name="see-also"></a>Voir aussi
- [Utiliser des feuilles de calcul](../vsto/working-with-worksheets.md)
- [Comment : imprimer des feuilles de calcul par programmation](../vsto/how-to-programmatically-print-worksheets.md)
- [Comment : supprimer des feuilles de calcul à partir de classeurs par programmation](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Comment : masquer des feuilles de calcul par programmation](../vsto/how-to-programmatically-hide-worksheets.md)
- [Comment : protéger des feuilles de calcul par programmation](../vsto/how-to-programmatically-protect-worksheets.md)
- [Élément hôte de feuille de calcul](../vsto/worksheet-host-item.md)
- [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
- [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
