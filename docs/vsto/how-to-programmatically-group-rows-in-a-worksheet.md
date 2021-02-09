---
title: 'Comment : regrouper des lignes dans une feuille de calcul par programmation'
description: Découvrez comment vous pouvez regrouper par programmation une ou plusieurs lignes entières dans Microsoft Excel à l’aide d’un contrôle NamedRange ou d’un objet de plage Excel natif.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: eaa0bbcc2c26a36e43e862cbe5a8f117c2a1fb26
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885415"
---
# <a name="how-to-programmatically-group-rows-in-a-worksheet"></a>Comment : regrouper des lignes dans une feuille de calcul par programmation
  Vous pouvez regrouper une ou plusieurs lignes entières. Pour créer un groupe dans une feuille de calcul, utilisez un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle ou un objet de plage Excel natif.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Utiliser un contrôle NamedRange
 Si vous ajoutez un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle à un projet au niveau du document au moment du design, vous pouvez utiliser le contrôle pour créer un groupe par programmation. L’exemple suivant suppose qu’il existe trois <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôles sur la même feuille de calcul : `data2001` , `data2002` et `dataAll` . Chaque plage nommée fait référence à une ligne entière dans la feuille de calcul.

### <a name="to-create-a-group-of-namedrange-controls-on-a-worksheet"></a>Pour créer un groupe de contrôles NamedRange dans une feuille de calcul

1. Regroupez trois plages nommées en appelant la <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> méthode de chaque plage. Ce code doit être placé dans une classe Sheet et non pas dans la classe `ThisWorkbook` .

     [!code-csharp[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#32)]

    > [!NOTE]
    > Pour dissocier des lignes, appelez la <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A> méthode.

## <a name="use-native-excel-ranges"></a>Utiliser des plages Excel natives
 Le code suppose que vous avez trois plages Excel nommées `data2001` , `data2002` et `dataAll` dans une feuille de calcul.

### <a name="to-create-a-group-of-excel-ranges-in-a-worksheet"></a>Pour créer un groupe de plages Excel dans une feuille de calcul

1. Regroupez trois plages nommées en appelant la <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> méthode de chaque plage. L’exemple suivant suppose qu’il existe trois <xref:Microsoft.Office.Interop.Excel.Range> contrôles nommés `data2001` , `data2002` et `dataAll` sur la même feuille de calcul. Chaque plage nommée fait référence à une ligne entière dans la feuille de calcul.

     [!code-csharp[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#33)]

    > [!NOTE]
    > Pour dissocier des lignes, appelez la <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A> méthode.

## <a name="see-also"></a>Voir aussi
- [Utiliser des feuilles de calcul](../vsto/working-with-worksheets.md)
- [NamedRange, contrôle](../vsto/namedrange-control.md)
- [Comment : ajouter des contrôles NamedRange aux feuilles de calcul](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
