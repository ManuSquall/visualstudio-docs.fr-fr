---
title: 'Comment : faire référence par programmation aux plages de feuille de calcul dans le code'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 608ce006ccc34330631da8d4c947405b027f1a1f
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35672781"
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>Comment : faire référence par programmation aux plages de feuille de calcul dans le code
  Vous utilisez un processus semblable pour faire référence au contenu d’un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle ou un objet de plage Excel natif.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="use-a-namedrange-control"></a>Utiliser un contrôle NamedRange  
 L’exemple suivant ajoute un <xref:Microsoft.Office.Tools.Excel.NamedRange> à une feuille de calcul, puis ajoute le texte à la cellule dans la plage.  
  
### <a name="to-refer-to-a-namedrange-control"></a>Pour faire référence à un contrôle NamedRange  
  
1.  Assignez une chaîne à la <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> propriété de la <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle. Ce code doit être placé dans une classe Sheet et non pas dans la classe `ThisWorkbook` .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#46)]  
  
## <a name="use-native-excel-ranges"></a>Utiliser des plages Excel natifs  
 L’exemple suivant ajoute une plage Excel native à une feuille de calcul, puis ajoute le texte à la cellule dans la plage.  
  
### <a name="to-refer-to-a-native-range-object"></a>Pour faire référence à un objet de plage native  
  
1.  Assignez une chaîne à la <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> propriété de la plage.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#47)]  
  
## <a name="see-also"></a>Voir aussi  
 [Travailler avec des plages](../vsto/working-with-ranges.md)   
 [Comment : vérifier l’orthographe dans les feuilles de calcul par programmation](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [Comment : appliquer des styles à des plages dans les classeurs par programmation](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Comment : remplir par programmation automatiquement des plages avec des données soumises à modification incrémentielle](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [Comment : rechercher du texte dans les plages de feuille de calcul par programmation](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)   
 [NamedRange (contrôle)](../vsto/namedrange-control.md)   
 [Éléments hôtes et la vue d’ensemble des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Limitations de programmation des éléments hôtes et contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  