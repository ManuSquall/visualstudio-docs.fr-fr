---
title: 'Procédure : Stocker et récupérer des valeurs de date dans des plages Excel par programmation'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 3a2354df7027f3aa73f13e830b9a85895e54c920
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63419286"
---
# <a name="how-to-programmatically-store-and-retrieve-date-values-in-excel-ranges"></a>Procédure : Stocker et récupérer des valeurs de date dans des plages Excel par programmation
  Vous pouvez stocker et récupérer des valeurs dans un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle ou un objet de plage Excel natif.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Si vous stockez une valeur de date qui se situe sur ou après le 1/1/1900 dans une plage à l’aide des outils de développement Office dans Visual Studio, il est stocké au format OLE Automation (OA). Vous devez utiliser le <xref:System.DateTime.FromOADate%2A> méthode pour récupérer la valeur de dates de OLE Automation (OA). Si la date est antérieure à 1/1/1900, il est stocké sous forme de chaîne.

> [!NOTE]
> Les dates Excel diffèrent des dates OLE Automation pour les deux premiers mois de 1900. Il existe également différences si la **système de dates 1904** option est activée. Les exemples de code ci-dessous ne traitent pas ces différences.

## <a name="use-a-namedrange-control"></a>Utiliser un contrôle NamedRange

- Cet exemple concerne des personnalisations au niveau du document. Le code suivant doit être placé dans une classe sheet et non dans le `ThisWorkbook` classe.

### <a name="to-store-a-date-value-in-a-named-range"></a>Pour stocker une valeur de date dans une plage nommée

1. Créer un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle à la cellule **A1**.

     [!code-csharp[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#50)]
     [!code-vb[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#50)]

2. Définir la date actuelle comme valeur pour `NamedRange1`.

     [!code-csharp[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#51)]
     [!code-vb[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#51)]

### <a name="to-retrieve-a-date-value-from-a-named-range"></a>Pour récupérer une valeur de date à partir d’une plage nommée

1. Récupérez la valeur de date de `NamedRange1`.

     [!code-csharp[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#52)]
     [!code-vb[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#52)]

## <a name="use-native-excel-ranges"></a>Utiliser des plages Excel natifs

### <a name="to-store-a-date-value-in-a-native-excel-range-object"></a>Pour stocker une valeur de date dans un objet de plage Excel natif

1. Créer un <xref:Microsoft.Office.Interop.Excel.Range> qui représente la cellule **A1**.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#25)]

2. Définir la date actuelle comme valeur pour `rng`.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#26)]

### <a name="to-retrieve-a-date-value-from-a-native-excel-range-object"></a>Pour récupérer une valeur de date à partir d’un objet de plage Excel natif

1. Récupérez la valeur de date de `rng`.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#27)]

## <a name="see-also"></a>Voir aussi
- [Travailler avec des plages](../vsto/working-with-ranges.md)
- [Vue d’ensemble du modèle d’objet Excel](../vsto/excel-object-model-overview.md)
- [NamedRange (contrôle)](../vsto/namedrange-control.md)
- [Guide pratique pour Faire référence par programmation aux plages de feuille de calcul dans le code](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Guide pratique pour Ajouter des contrôles NamedRange aux feuilles de calcul](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
