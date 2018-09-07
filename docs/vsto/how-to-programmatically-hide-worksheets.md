---
title: 'Comment : masquer des feuilles de calcul par programmation'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden worksheets
- worksheets, hiding
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a60a0189af5608496e1f0f415a2d668e896af8e3
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673629"
---
# <a name="how-to-programmatically-hide-worksheets"></a>Comment : masquer des feuilles de calcul par programmation
  Vous pouvez afficher ou masquer une feuille de calcul dans un classeur. Pour masquer une feuille de calcul, utilisez l’élément hôte de feuille de calcul ou accédez à la feuille de calcul à l’aide de la collection Sheets du classeur.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="use-the-worksheet-host-item"></a>Utilisez l’élément hôte de feuille de calcul  
 Si la feuille de calcul a été ajoutée au moment du design dans une personnalisation au niveau du document, utilisez la propriété <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> pour masquer la feuille de calcul spécifiée.  
  
### <a name="to-hide-a-worksheet-using-a-worksheet-host-item"></a>Pour masquer une feuille de calcul à l’aide d’un élément hôte de feuille de calcul  
  
1.  Affectez à la propriété <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> de l’élément hôte `Sheet1` la valeur d’énumération <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#25)]  
  
## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Utilisez la collection Sheets du classeur Excel  
 Accédez aux feuilles de calcul via la collection <xref:Microsoft.Office.Interop.Excel.Sheets> Microsoft Office Excel dans les cas suivants :  
  
-   Vous souhaitez masquer une feuille de calcul dans un composant logiciel complément VSTO.  
  
-   La feuille de calcul à masquer a été créée au moment de l’exécution dans une personnalisation au niveau du document.  
  
### <a name="to-hide-a-worksheet-using-the-sheets-collection-of-the-excel-workbook"></a>Pour masquer une feuille de calcul à l’aide de la collection Sheets du classeur Excel  
  
1.  Affectez à la propriété <xref:Microsoft.Office.Interop.Excel.Worksheets.Visible%2A> de la feuille de calcul la valeur d’énumération <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#26)]  
  
## <a name="see-also"></a>Voir aussi  
 [Travailler avec des feuilles de calcul](../vsto/working-with-worksheets.md)   
 [Comment : supprimer par programmation des feuilles de calcul des classeurs](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Comment : déplacer des feuilles de calcul dans les classeurs par programmation](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [Comment : protéger des feuilles de calcul par programmation](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Éléments hôtes et la vue d’ensemble des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)  
  