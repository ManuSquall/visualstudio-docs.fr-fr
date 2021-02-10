---
title: 'Comment : faire référence aux plages de la feuille de calcul dans le code par programmation'
description: Découvrez comment vous pouvez utiliser Visual Studio pour faire référence par programmation au contenu d’un contrôle NamedRange ou d’un objet Range Excel natif dans une feuille de calcul Microsoft Excel.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, referring to
- worksheets, referring to ranges
- referring to worksheet ranges
- Excel [Office development in Visual Studio], referring to worksheet ranges
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 89a4b7c594f942405777145f94ed0a3503e9b16f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963755"
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>Comment : faire référence aux plages de la feuille de calcul dans le code par programmation
  Vous utilisez un processus similaire pour faire référence au contenu d’un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle ou d’un objet de plage Excel natif.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Utiliser un contrôle NamedRange
 L’exemple suivant ajoute un <xref:Microsoft.Office.Tools.Excel.NamedRange> à une feuille de calcul, puis ajoute du texte à la cellule dans la plage.

### <a name="to-refer-to-a-namedrange-control"></a>Pour faire référence à un contrôle NamedRange

1. Assignez une chaîne à la <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> propriété du <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle. Ce code doit être placé dans une classe Sheet et non pas dans la classe `ThisWorkbook` .

     [!code-csharp[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#46)]

## <a name="use-native-excel-ranges"></a>Utiliser des plages Excel natives
 L’exemple suivant ajoute une plage Excel native à une feuille de calcul, puis ajoute du texte à la cellule de la plage.

### <a name="to-refer-to-a-native-range-object"></a>Pour faire référence à un objet Range natif

1. Assignez une chaîne à la <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> propriété de la plage.

     [!code-csharp[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#47)]

## <a name="see-also"></a>Voir aussi
- [Utiliser des plages](../vsto/working-with-ranges.md)
- [Comment : vérifier l’orthographe dans les feuilles de calcul par programmation](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [Comment : appliquer des styles à des plages dans des classeurs par programmation](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Comment : remplir automatiquement des plages par programmation avec des données à modification incrémentielle](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)
- [Comment : Rechercher du texte dans les plages de la feuille de calcul par programmation](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)
- [NamedRange, contrôle](../vsto/namedrange-control.md)
- [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
- [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
