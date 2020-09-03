---
title: 'Comment : appliquer une couleur à des plages Excel par programmation'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- color, Excel ranges
- ranges, applying color
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0d4a99e2e71e6a87b304ceea45a3cd595f911ff1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543453"
---
# <a name="how-to-programmatically-apply-color-to-excel-ranges"></a>Comment : appliquer une couleur à des plages Excel par programmation
  Pour appliquer une couleur à du texte dans une plage de cellules, utilisez un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle ou un objet de plage Excel natif.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Utiliser un contrôle NamedRange
 Cet exemple est destiné aux personnalisations au niveau du document.

### <a name="to-apply-color-to-a-namedrange-control"></a>Pour appliquer la couleur à un contrôle NamedRange

1. Créez un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle à la cellule a1.

     [!code-csharp[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#65)]
     [!code-vb[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#65)]

2. Définissez la couleur du texte dans le <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle.

     [!code-csharp[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#66)]
     [!code-vb[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#66)]

## <a name="use-native-excel-ranges"></a>Utiliser des plages Excel natives

### <a name="to-apply-color-to-a-native-excel-range-object"></a>Pour appliquer la couleur à un objet de plage Excel natif

1. Créez une plage à la cellule a1, puis définissez la couleur du texte.

     [!code-csharp[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#67)]
     [!code-vb[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#67)]

## <a name="see-also"></a>Voir aussi
- [Utiliser des plages](../vsto/working-with-ranges.md)
- [NamedRange, contrôle](../vsto/namedrange-control.md)
- [Comment : appliquer des styles à des plages dans des classeurs par programmation](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Comment : faire référence aux plages de la feuille de calcul dans le code par programmation](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Automatiser Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
