---
title: "Comment : faire référence par programmation aux plages de feuille de calcul dans le Code | Documents Microsoft"
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
- ranges, referring to
- worksheets, referring to ranges
- referring to worksheet ranges
- Excel [Office development in Visual Studio], referring to worksheet ranges
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 001efb4609059ba68a0a6a5f9c30d2f416805013
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>Comment : faire référence aux plages de la feuille de calcul dans le code par programmation
  Vous utilisez un processus similaire pour faire référence au contenu d’un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle ou un objet de plage Excel natif.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-a-namedrange-control"></a>À l’aide d’un contrôle NamedRange  
 L’exemple suivant ajoute une <xref:Microsoft.Office.Tools.Excel.NamedRange> à une feuille de calcul, puis ajoute du texte à la cellule de la plage.  
  
#### <a name="to-refer-to-a-namedrange-control"></a>Pour faire référence à un contrôle NamedRange  
  
1.  Attribuez une chaîne à la <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> propriété de la <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle. Ce code doit être placé dans une classe Sheet et non pas dans la classe `ThisWorkbook` .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#46)]  
  
## <a name="using-native-excel-ranges"></a>À l’aide de plages Excel natives  
 L’exemple suivant ajoute une plage Excel native à une feuille de calcul et puis ajoute du texte à la cellule dans la plage.  
  
#### <a name="to-refer-to-a-native-range-object"></a>Pour faire référence à un objet de plage native  
  
1.  Attribuez une chaîne à la <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> propriété de la plage.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#47)]  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des plages](../vsto/working-with-ranges.md)   
 [Comment : vérifier l’orthographe dans les feuilles de calcul par programmation](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [Comment : appliquer des Styles à des plages dans les classeurs par programmation](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Comment : remplir par programme automatiquement des plages avec des données soumises à modification incrémentielle](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [Comment : rechercher le texte dans les plages de feuille de calcul par programmation](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)   
 [NamedRange (contrôle)](../vsto/namedrange-control.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  