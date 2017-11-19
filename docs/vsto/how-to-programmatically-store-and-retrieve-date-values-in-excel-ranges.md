---
title: "Comment : stocker par programme et récupérer des valeurs de Date dans des plages Excel | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
ms.assetid: e1cdd262-0356-4499-8bc5-e730f74235a2
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4d19de6848da22238dc1cf394fa3d417ea0d8c88
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-store-and-retrieve-date-values-in-excel-ranges"></a>Comment : stocker et récupérer des valeurs de date dans des plages Excel par programmation
  Vous pouvez stocker et récupérer des valeurs dans un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle ou un objet de plage Excel natif.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Si vous stockez une valeur de date qui se situe sur ou après le 1/1/1900 dans une plage à l’aide des outils de développement Office dans Visual Studio, il est stocké dans le format OLE Automation (OA). Vous devez utiliser le <xref:System.DateTime.FromOADate%2A> pour récupérer la valeur des dates de OLE Automation (OA). Si la date est antérieure à 1/1/1900, il est stocké sous forme de chaîne.  
  
> [!NOTE]  
>  Les dates Excel diffèrent des dates OLE Automation pour les deux premiers mois de 1900. Il existe également les différences si la **système de date 1904** option est activée. Les exemples de code ci-dessous ne traitent pas ces différences.  
  
## <a name="using-a-namedrange-control"></a>À l’aide d’un contrôle NamedRange  
  
-   Cet exemple est pour les personnalisations au niveau du document. Le code suivant doit être placé dans une classe sheet et non pas dans le `ThisWorkbook` classe.  
  
#### <a name="to-store-a-date-value-in-a-named-range"></a>Pour stocker une valeur de date dans une plage nommée  
  
1.  Créer un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle à la cellule **A1**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#50)]
     [!code-vb[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#50)]  
  
2.  Définir la date actuelle en tant que la valeur de `NamedRange1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#51)]
     [!code-vb[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#51)]  
  
#### <a name="to-retrieve-a-date-value-from-a-named-range"></a>Pour récupérer une valeur de date à partir d’une plage nommée  
  
1.  Récupérer la valeur de date à partir de `NamedRange1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#52)]
     [!code-vb[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#52)]  
  
## <a name="using-native-excel-ranges"></a>À l’aide de plages Excel natives  
  
#### <a name="to-store-a-date-value-in-a-native-excel-range-object"></a>Pour stocker une valeur de date dans un objet de plage Excel natif  
  
1.  Créer un <xref:Microsoft.Office.Interop.Excel.Range> qui représente la cellule **A1**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#25)]  
  
2.  Définir la date actuelle en tant que la valeur de `rng`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#26)]  
  
#### <a name="to-retrieve-a-date-value-from-a-native-excel-range-object"></a>Pour récupérer une valeur de date à partir d’un objet de plage Excel natif  
  
1.  Récupérer la valeur de date à partir de `rng`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#27)]  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des plages](../vsto/working-with-ranges.md)   
 [Vue d’ensemble du modèle d’objet Excel](../vsto/excel-object-model-overview.md)   
 [NamedRange (contrôle)](../vsto/namedrange-control.md)   
 [Comment : faire référence par programmation aux plages de feuille de calcul dans le Code](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Comment : ajouter des contrôles NamedRange aux feuilles de calcul](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  