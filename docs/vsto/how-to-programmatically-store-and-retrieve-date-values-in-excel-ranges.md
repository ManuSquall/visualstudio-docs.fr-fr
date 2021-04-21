---
title: Stocker & récupérer des valeurs de date dans des plages Excel par programmation
description: Découvrez comment vous pouvez utiliser Visual Studio pour stocker et récupérer par programme des valeurs de date dans des plages Microsoft Excel.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6e3115e00147a5dff850f6e0c051ffc3b6733218
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826237"
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

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet50":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet50":::

2. Définissez la date du jour comme valeur pour `NamedRange1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet51":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet51":::

### <a name="to-retrieve-a-date-value-from-a-named-range"></a>Pour récupérer une valeur de date à partir d’une plage nommée

1. Récupérez la valeur de date à partir de `NamedRange1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet52":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet52":::

## <a name="use-native-excel-ranges"></a>Utiliser des plages Excel natives

### <a name="to-store-a-date-value-in-a-native-excel-range-object"></a>Pour stocker une valeur de date dans un objet de plage Excel natif

1. Créez un <xref:Microsoft.Office.Interop.Excel.Range> qui représente la cellule **a1**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet25":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet25":::

2. Définissez la date du jour comme valeur pour `rng` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet26":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet26":::

### <a name="to-retrieve-a-date-value-from-a-native-excel-range-object"></a>Pour récupérer une valeur de date à partir d’un objet de plage Excel natif

1. Récupérez la valeur de date à partir de `rng` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet27":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet27":::

## <a name="see-also"></a>Voir aussi
- [Utiliser des plages](../vsto/working-with-ranges.md)
- [Vue d’ensemble du modèle objet Excel](../vsto/excel-object-model-overview.md)
- [NamedRange, contrôle](../vsto/namedrange-control.md)
- [Comment : faire référence aux plages de la feuille de calcul dans le code par programmation](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Comment : ajouter des contrôles NamedRange aux feuilles de calcul](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
