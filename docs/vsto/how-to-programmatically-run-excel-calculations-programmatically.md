---
title: 'Procédure : Exécuter des calculs Excel par programmation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, running calculations
- calculations, running in Excel
- Excel [Office development in Visual Studio], running calculations programmatically
- workbooks, running calculations
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 82e2cbd2f3e74e50c7ff01f6943fdb62e11f1525
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53821059"
---
# <a name="how-to-programmatically-run-excel-calculations"></a>Procédure : Exécuter des calculs Excel par programmation  
  Vous utilisez un processus similaire pour exécuter des calculs un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle ou un objet de plage Excel natif.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="run-calculations-in-a-namedrange-control"></a>Exécuter des calculs dans un contrôle NamedRange  
 L’exemple suivant crée un <xref:Microsoft.Office.Tools.Excel.NamedRange> à la cellule A1, puis calcule la cellule. Ce code doit être placé dans une classe Sheet et non pas dans la classe `ThisWorkbook` .  
  
### <a name="to-run-calculations-in-a-namedrange-control"></a>Pour exécuter des calculs dans un contrôle NamedRange  
  
1.  Créez la plage nommée.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#75](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#75)]
     [!code-vb[Trin_VstcoreExcelAutomation#75](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#75)]  
  
2.  Appelez le <xref:Microsoft.Office.Tools.Excel.NamedRange.Calculate%2A> méthode de la plage spécifiée.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#76](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#76)]
     [!code-vb[Trin_VstcoreExcelAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#76)]  
  
## <a name="run-calculations-in-a-native-excel-range"></a>Exécuter des calculs dans une plage Excel native  
  
### <a name="to-run-calculations-in-a-native-excel-range"></a>Pour exécuter des calculs dans une plage Excel native  
  
1.  Créez la plage nommée.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#30](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#30](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#30)]  
  
2.  Appelez le <xref:Microsoft.Office.Interop.Excel.Range.Calculate%2A> méthode de la plage spécifiée.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#31](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#31](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#31)]  
  
## <a name="see-also"></a>Voir aussi  
 [Travailler avec des plages](../vsto/working-with-ranges.md)   
 [NamedRange (contrôle)](../vsto/namedrange-control.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
