---
title: Stocker & récupérer des valeurs de date dans des plages Excel par programmation
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], retrieving date values from ranges
- ranges, retrieving data values
- dates, retrieving from Excel ranges
- Excel [Office development in Visual Studio], storing date values in ranges
- date values, storing in Excel ranges
- dates, storing in Excel ranges
- ranges, storing date values
- date values
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c2bd76d37a9c9b6e51de7bbe01b54d1be6c93128
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91583773"
---
# <a name="how-to-programmatically-store-and-retrieve-date-values-in-excel-ranges"></a>Comment : stocker et récupérer des valeurs de date dans des plages Excel par programmation
  Vous pouvez stocker et récupérer des valeurs dans un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle ou un objet de plage Excel natif.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Si vous stockez une valeur de date comprise ou après 1/1/1900 dans une plage à l’aide des outils de développement Office dans Visual Studio, elle est stockée au format OLE Automation (OA). Vous devez utiliser la <xref:System.DateTime.FromOADate%2A> méthode pour récupérer la valeur des dates OLE Automation (OA). Si la date est antérieure à 1/1/1900, elle est stockée sous la forme d’une chaîne.

> [!NOTE]
> Les dates Excel diffèrent des dates OLE Automation des deux premiers mois de 1900. Il existe également des différences si l’option de **système de date 1904** est cochée. Les exemples de code ci-dessous ne traitent pas ces différences.

## <a name="use-a-namedrange-control"></a>Utiliser un contrôle NamedRange

- Cet exemple est destiné aux personnalisations au niveau du document. Le code suivant doit être placé dans une classe Sheet et non dans la `ThisWorkbook` classe.

### <a name="to-store-a-date-value-in-a-named-range"></a>Pour stocker une valeur de date dans une plage nommée

1. Créez un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle à la cellule **a1**.

     [!code-csharp[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#50)]
     [!code-vb[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#50)]

2. Définissez la date du jour comme valeur pour `NamedRange1` .

     [!code-csharp[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#51)]
     [!code-vb[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#51)]

### <a name="to-retrieve-a-date-value-from-a-named-range"></a>Pour récupérer une valeur de date à partir d’une plage nommée

1. Récupérez la valeur de date à partir de `NamedRange1` .

     [!code-csharp[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#52)]
     [!code-vb[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#52)]

## <a name="use-native-excel-ranges"></a>Utiliser des plages Excel natives

### <a name="to-store-a-date-value-in-a-native-excel-range-object"></a>Pour stocker une valeur de date dans un objet de plage Excel natif

1. Créez un <xref:Microsoft.Office.Interop.Excel.Range> qui représente la cellule **a1**.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#25)]

2. Définissez la date du jour comme valeur pour `rng` .

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#26)]

### <a name="to-retrieve-a-date-value-from-a-native-excel-range-object"></a>Pour récupérer une valeur de date à partir d’un objet de plage Excel natif

1. Récupérez la valeur de date à partir de `rng` .

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#27)]

## <a name="see-also"></a>Voir aussi
- [Utiliser des plages](../vsto/working-with-ranges.md)
- [Vue d’ensemble du modèle objet Excel](../vsto/excel-object-model-overview.md)
- [NamedRange, contrôle](../vsto/namedrange-control.md)
- [Comment : faire référence aux plages de la feuille de calcul dans le code par programmation](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Comment : ajouter des contrôles NamedRange aux feuilles de calcul](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
