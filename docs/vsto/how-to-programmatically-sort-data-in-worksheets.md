---
title: "Comment : trier par programme les données dans des feuilles de calcul | Documents Microsoft"
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
- data sorting, worksheets
- data [Office development in Visual Studio], sorting in worksheets
- worksheets, sorting data
- sorting data, in worksheets
ms.assetid: 2fbc6e63-02ea-4624-8d6f-bed60e06c61e
caps.latest.revision: "56"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 211a357095290f8f8d608d01c093cd373c7525ab
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-sort-data-in-worksheets"></a>Comment : trier les données par programmation dans les feuilles de calcul
  Vous pouvez trier les données contenues dans les listes et les plages de feuille de calcul au moment de l'exécution. Le code suivant trie une plage à colonnes multiples nommée `Fruits` sur les données de la première colonne, puis sur les données de la deuxième colonne.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="sorting-data-in-a-document-level-customization"></a>Tri des données dans une personnalisation au niveau du document  
  
#### <a name="to-sort-data-in-a-namedrange-control"></a>Pour trier les des données d'un contrôle NamedRange  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Excel.NamedRange.Sort%2A> du contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange>. L'exemple suivant requiert un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> nommé `Fruits` sur une feuille de calcul. Ce code doit être placé dans une classe Sheet et non pas dans la classe `ThisWorkbook` .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#78)]
     [!code-vb[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#78)]  
  
 Placez le code suivant dans Sheet1.vb ou Sheet1.cs pour trier les données d'un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject>. Le code suppose que vous avez un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> nommé `fruitList` dans une feuille de calcul nommée `Sheet1`.  
  
#### <a name="to-sort-data-in-a-listobject-control"></a>Pour trier les données d'un contrôle ListObject  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> de la propriété <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> du contrôle hôte <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#79)]
     [!code-vb[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#79)]  
  
## <a name="sorting-data-in-a-vsto-add-in"></a>Tri de données dans un complément VSTO  
  
#### <a name="to-sort-data-in-a-native-range"></a>Pour trier les données d'une plage native  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> du contrôle Excel <xref:Microsoft.Office.Interop.Excel.Range> natif. L'exemple suivant requiert un contrôle Excel nommé `Fruits` sur une feuille de calcul.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#23)]  
  
#### <a name="to-sort-data-in-a-listobject-control"></a>Pour trier les données d'un contrôle ListObject  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> de la propriété <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> du contrôle Excel <xref:Microsoft.Office.Interop.Excel.ListObject> natif. L'exemple suivant suppose que vous disposez d'un contrôle Excel <xref:Microsoft.Office.Interop.Excel.ListObject> natif nommé `fruitList` dans la feuille de calcul active.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#24)]  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des feuilles de calcul](../vsto/working-with-worksheets.md)   
 [Comment : remplir par programme automatiquement des plages avec des données soumises à modification incrémentielle](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [Comment : faire référence par programmation aux plages de feuille de calcul dans le Code](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Comment : appliquer des Styles à des plages dans les classeurs par programmation](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [NamedRange (contrôle)](../vsto/namedrange-control.md)   
 [ListObject (contrôle)](../vsto/listobject-control.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  