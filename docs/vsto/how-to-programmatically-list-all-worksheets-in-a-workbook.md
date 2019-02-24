---
title: 'Procédure : Répertorier par programmation toutes les feuilles de calcul dans un classeur'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, listing worksheets
- worksheets, listing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c9f6a27ea1f8d6c50b4b9b8eba07186f34eb143b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56616636"
---
# <a name="how-to-programmatically-list-all-worksheets-in-a-workbook"></a>Procédure : Répertorier par programmation toutes les feuilles de calcul dans un classeur
  La classe <xref:Microsoft.Office.Interop.Excel.Workbook> fournit un objet <xref:Microsoft.Office.Interop.Excel.Worksheets>. Cet objet contient une collection de tous les objets <xref:Microsoft.Office.Interop.Excel.Worksheet> du classeur spécifié.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-document-level-customization"></a>Pour répertorier toutes les feuilles de calcul existantes dans un classeur dans une personnalisation au niveau du document

1.  Itérez au sein de la collection <xref:Microsoft.Office.Interop.Excel.Worksheets> et envoyez le nom de chaque feuille vers une cellule décalée par un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange>.

     [!code-csharp[Trin_VstcoreExcelAutomation#21](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomation#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#21)]

## <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-vsto-add-in"></a>Pour répertorier toutes les feuilles de calcul existantes d’un classeur dans un complément VSTO

1.  Itérez au sein de la collection <xref:Microsoft.Office.Interop.Excel.Worksheets> et envoyez le nom de chaque feuille vers une cellule décalée par un objet <xref:Microsoft.Office.Interop.Excel.Range>.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#13)]

## <a name="see-also"></a>Voir aussi
- [Travailler avec des feuilles de calcul](../vsto/working-with-worksheets.md)
- [Guide pratique pour Ajouter par programmation des feuilles de calcul à des classeurs](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Guide pratique pour Déplacer des feuilles de calcul dans les classeurs par programmation](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)
- [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)
