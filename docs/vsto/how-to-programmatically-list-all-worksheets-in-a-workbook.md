---
title: 'Comment : répertorier par programmation toutes les feuilles de calcul dans un classeur'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, listing worksheets
- worksheets, listing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bb82b26fedce0590c5c2fe9cfa1b321fef5dbf19
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257759"
---
# <a name="how-to-programmatically-list-all-worksheets-in-a-workbook"></a>Comment : répertorier par programmation toutes les feuilles de calcul dans un classeur
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
 [Travailler avec des feuilles de calcul](../vsto/working-with-worksheets.md)   
 [Comment : ajouter par programmation des feuilles de calcul à des classeurs](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Comment : déplacer des feuilles de calcul dans les classeurs par programmation](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)  
  
  