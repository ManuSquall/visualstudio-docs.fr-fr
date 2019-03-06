---
title: 'Procédure : Regrouper des lignes dans une feuille de calcul par programmation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, creating groups
- groups, creating in worksheets
- ranges, creating groups
- worksheets, clearing groups
- groups
- groups [Office development in Visual Studio], clearing in worksheets
- worksheets, ungrouping rows and columns
- rows [Office development in Visual Studio], ungrouping
- columns [Office development in Visual Studio], ungrouping
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f2ff75594cd3c1eb560f9cded5dad2a764198fb5
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56598227"
---
# <a name="how-to-programmatically-group-rows-in-a-worksheet"></a>Procédure : Regrouper des lignes dans une feuille de calcul par programmation
  Vous pouvez regrouper un ou plusieurs lignes entières. Pour créer un groupe dans une feuille de calcul, utilisez un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle ou un objet de plage Excel natif.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Utiliser un contrôle NamedRange
 Si vous ajoutez un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle à un projet au niveau du document au moment du design, vous pouvez utiliser le contrôle à créer par programmation un groupe. L’exemple suivant suppose qu’il existe trois <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôles sur la feuille de calcul : `data2001`, `data2002`, et `dataAll`. Chaque plage nommée fait référence à une ligne entière dans la feuille de calcul.

### <a name="to-create-a-group-of-namedrange-controls-on-a-worksheet"></a>Pour créer un groupe de contrôles NamedRange sur une feuille de calcul

1.  Regrouper les trois plages nommées en appelant le <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> méthode de chaque plage. Ce code doit être placé dans une classe Sheet et non pas dans la classe `ThisWorkbook` .

     [!code-csharp[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#32)]

    > [!NOTE]
    >  Pour dissocier des lignes, appelez le <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A> (méthode).

## <a name="use-native-excel-ranges"></a>Utiliser des plages Excel natifs
 Le code suppose que vous avez trois plages Excel nommés `data2001`, `data2002`, et `dataAll` sur une feuille de calcul.

### <a name="to-create-a-group-of-excel-ranges-in-a-worksheet"></a>Pour créer un groupe de plages Excel dans une feuille de calcul

1.  Regrouper les trois plages nommées en appelant le <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> méthode de chaque plage. L’exemple suivant suppose qu’il existe trois <xref:Microsoft.Office.Interop.Excel.Range> contrôles nommés `data2001`, `data2002`, et `dataAll` sur la feuille de calcul. Chaque plage nommée fait référence à une ligne entière dans la feuille de calcul.

     [!code-csharp[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#33)]

    > [!NOTE]
    >  Pour dissocier des lignes, appelez le <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A> (méthode).

## <a name="see-also"></a>Voir aussi
- [Travailler avec des feuilles de calcul](../vsto/working-with-worksheets.md)
- [NamedRange (contrôle)](../vsto/namedrange-control.md)
- [Guide pratique pour Ajouter des contrôles NamedRange aux feuilles de calcul](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
