---
title: 'Procédure : Sélectionner des feuilles de calcul par programmation'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 20ebc8fea14b3dc52c802543f97318ec7fae7529
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255629"
---
# <a name="how-to-programmatically-select-worksheets"></a>Procédure : Sélectionner des feuilles de calcul par programmation
  La méthode <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> méthode sélectionne l'objet spécifié, ce qui déplace la sélection de l'utilisateur vers le nouvel objet. Utilisez la méthode <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A> si vous souhaitez donner le focus à l'objet sans modifier la sélection de l'utilisateur.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Si vous souhaitez sélectionner une feuille de calcul existante dans un complément VSTO ou si la feuille de calcul a été créée au moment de l'exécution dans une personnalisation au niveau du document, vous devez utiliser la collection Excel <xref:Microsoft.Office.Interop.Excel.Sheets> du classeur Excel pour y accéder. Sinon, vous pouvez accéder directement à l'élément hôte <xref:Microsoft.Office.Tools.Excel.Worksheet>.

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
- [Guide pratique pour Imprimer des feuilles de calcul par programmation](../vsto/how-to-programmatically-print-worksheets.md)
- [Guide pratique pour Supprimer par programmation des feuilles de calcul des classeurs](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Guide pratique pour Masquer les feuilles de calcul par programmation](../vsto/how-to-programmatically-hide-worksheets.md)
- [Guide pratique pour Protéger des feuilles de calcul par programmation](../vsto/how-to-programmatically-protect-worksheets.md)
- [Élément hôte de feuille de calcul](../vsto/worksheet-host-item.md)
- [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
- [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
