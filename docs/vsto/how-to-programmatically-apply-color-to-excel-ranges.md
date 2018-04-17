---
title: 'Comment : appliquer une couleur aux plages Excel par programmation | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- color, Excel ranges
- ranges, applying color
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b518cfb4f1ef7c5d757e4a68bbc12b51c6c61ae3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-apply-color-to-excel-ranges"></a>Comment : appliquer de la couleur à des plages Excel par programmation
  Pour appliquer une couleur à du texte dans une plage de cellules, utilisez un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle ou un objet de plage Excel natif.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-a-namedrange-control"></a>À l’aide d’un contrôle NamedRange  
 Cet exemple est pour les personnalisations au niveau du document.  
  
#### <a name="to-apply-color-to-a-namedrange-control"></a>Pour appliquer une couleur à un contrôle NamedRange  
  
1.  Créer un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle à la cellule A1.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#65)]
     [!code-vb[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#65)]  
  
2.  Définir la couleur du texte dans le <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#66)]
     [!code-vb[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#66)]  
  
## <a name="using-native-excel-ranges"></a>À l’aide de plages Excel natives  
  
#### <a name="to-apply-color-to-a-native-excel-range-object"></a>Pour appliquer une couleur à un objet de plage Excel natif  
  
1.  Créer une plage à la cellule A1, puis définissez la couleur du texte.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#67)]
     [!code-vb[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#67)]  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des plages](../vsto/working-with-ranges.md)   
 [NamedRange (contrôle)](../vsto/namedrange-control.md)   
 [Comment : appliquer des Styles à des plages dans les classeurs par programmation](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Comment : faire référence par programmation aux plages de feuille de calcul dans le Code](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Automatisation d’Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  