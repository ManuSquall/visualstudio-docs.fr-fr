---
title: 'Procédure : Appliquer de la couleur à des plages Excel par programmation'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 56ecbfcdaf22132f63df1ecf5eadba97dee426af
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62817271"
---
# <a name="how-to-programmatically-apply-color-to-excel-ranges"></a>Procédure : Appliquer de la couleur à des plages Excel par programmation
  Pour appliquer une couleur au texte dans une plage de cellules, utilisez un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle ou un objet de plage Excel natif.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Utiliser un contrôle NamedRange
 Cet exemple concerne des personnalisations au niveau du document.

### <a name="to-apply-color-to-a-namedrange-control"></a>Pour appliquer la couleur à un contrôle NamedRange

1. Créer un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle à la cellule A1.

     [!code-csharp[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#65)]
     [!code-vb[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#65)]

2. Définir la couleur du texte dans le <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle.

     [!code-csharp[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#66)]
     [!code-vb[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#66)]

## <a name="use-native-excel-ranges"></a>Utiliser des plages Excel natifs

### <a name="to-apply-color-to-a-native-excel-range-object"></a>Pour appliquer des couleurs à un objet de plage Excel natif

1. Créer une plage à la cellule A1, puis définissez la couleur du texte.

     [!code-csharp[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#67)]
     [!code-vb[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#67)]

## <a name="see-also"></a>Voir aussi
- [Travailler avec des plages](../vsto/working-with-ranges.md)
- [NamedRange (contrôle)](../vsto/namedrange-control.md)
- [Guide pratique pour Appliquer des styles à des plages dans les classeurs par programmation](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Guide pratique pour Faire référence par programmation aux plages de feuille de calcul dans le code](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Automatiser Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)
- [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
