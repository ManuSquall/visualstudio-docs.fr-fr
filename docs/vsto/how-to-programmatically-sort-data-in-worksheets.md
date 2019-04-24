---
title: 'Procédure : Trier les données dans des feuilles de calcul par programmation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data sorting, worksheets
- data [Office development in Visual Studio], sorting in worksheets
- worksheets, sorting data
- sorting data, in worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eeef19a04245d74d99050930cc3f66da627ffdd9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60111166"
---
# <a name="how-to-programmatically-sort-data-in-worksheets"></a>Procédure : Trier les données dans des feuilles de calcul par programmation
  Vous pouvez trier les données contenues dans les listes et les plages de feuille de calcul au moment de l'exécution. Le code suivant trie une plage à colonnes multiples nommée `Fruits` sur les données de la première colonne, puis sur les données de la deuxième colonne.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="sort-data-in-a-document-level-customization"></a>Trier des données dans une personnalisation au niveau du document

### <a name="to-sort-data-in-a-namedrange-control"></a>Pour trier les des données d'un contrôle NamedRange

1. Appelez la méthode <xref:Microsoft.Office.Tools.Excel.NamedRange.Sort%2A> du contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange>. L'exemple suivant requiert un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> nommé `Fruits` sur une feuille de calcul. Ce code doit être placé dans une classe Sheet et non pas dans la classe `ThisWorkbook` .

    [!code-csharp[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#78)]
    [!code-vb[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#78)]

   Placez le code suivant dans *Sheet1.vb* ou *Sheet1.cs* pour trier les données dans un <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle. Le code suppose que vous avez un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> nommé `fruitList` dans une feuille de calcul nommée `Sheet1`.

### <a name="to-sort-data-in-a-listobject-control"></a>Pour trier les données d'un contrôle ListObject

1. Appelez la méthode <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> de la propriété <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> du contrôle hôte <xref:Microsoft.Office.Tools.Excel.ListObject>.

     [!code-csharp[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#79)]
     [!code-vb[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#79)]

## <a name="sort-data-in-a-vsto-add-in"></a>Trier des données dans un complément, VSTO

### <a name="to-sort-data-in-a-native-range"></a>Pour trier les données d'une plage native

1. Appelez la méthode <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> du contrôle Excel <xref:Microsoft.Office.Interop.Excel.Range> natif. L'exemple suivant requiert un contrôle Excel nommé `Fruits` sur une feuille de calcul.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#23)]

### <a name="to-sort-data-in-a-listobject-control"></a>Pour trier les données d'un contrôle ListObject

1. Appelez la méthode <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> de la propriété <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> du contrôle Excel <xref:Microsoft.Office.Interop.Excel.ListObject> natif. L'exemple suivant suppose que vous disposez d'un contrôle Excel <xref:Microsoft.Office.Interop.Excel.ListObject> natif nommé `fruitList` dans la feuille de calcul active.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#24)]

## <a name="see-also"></a>Voir aussi
- [Travailler avec des feuilles de calcul](../vsto/working-with-worksheets.md)
- [Guide pratique pour Remplir par programmation automatiquement des plages avec des données soumises à modification incrémentielle](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)
- [Guide pratique pour Faire référence par programmation aux plages de feuille de calcul dans le code](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Guide pratique pour Appliquer des styles à des plages dans les classeurs par programmation](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [NamedRange (contrôle)](../vsto/namedrange-control.md)
- [ListObject (contrôle)](../vsto/listobject-control.md)
- [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
