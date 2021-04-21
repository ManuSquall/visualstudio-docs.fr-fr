---
title: 'Comment : trier des données dans des feuilles de calcul par programmation'
description: Découvrez comment vous pouvez utiliser Visual Studio pour trier par programmation les données contenues dans les plages et les listes de feuille de calcul au moment de l’exécution.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 024bf53b7fc7f3a6e32e10b7107c9a62d8c40cee
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825015"
---
# <a name="how-to-programmatically-sort-data-in-worksheets"></a>Comment : trier des données dans des feuilles de calcul par programmation
  Vous pouvez trier les données contenues dans les listes et les plages de feuille de calcul au moment de l'exécution. Le code suivant trie une plage à colonnes multiples nommée `Fruits` sur les données de la première colonne, puis sur les données de la deuxième colonne.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="sort-data-in-a-document-level-customization"></a>Trier des données dans une personnalisation au niveau du document

### <a name="to-sort-data-in-a-namedrange-control"></a>Pour trier les des données d'un contrôle NamedRange

1. Appelez la méthode <xref:Microsoft.Office.Tools.Excel.NamedRange.Sort%2A> du contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange>. L'exemple suivant requiert un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> nommé `Fruits` sur une feuille de calcul. Ce code doit être placé dans une classe Sheet et non pas dans la classe `ThisWorkbook` .

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet78":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet78":::

   Placez le code suivant dans *Feuil1. vb* ou *Feuil1. cs* pour trier les données dans un <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle. Le code suppose que vous avez un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> nommé `fruitList` dans une feuille de calcul nommée `Sheet1`.

### <a name="to-sort-data-in-a-listobject-control"></a>Pour trier les données d'un contrôle ListObject

1. Appelez la méthode <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> de la propriété <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> du contrôle hôte <xref:Microsoft.Office.Tools.Excel.ListObject>.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet79":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet79":::

## <a name="sort-data-in-a-vsto-add-in"></a>Trier des données dans un complément VSTO

### <a name="to-sort-data-in-a-native-range"></a>Pour trier les données d'une plage native

1. Appelez la méthode <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> du contrôle Excel <xref:Microsoft.Office.Interop.Excel.Range> natif. L'exemple suivant requiert un contrôle Excel nommé `Fruits` sur une feuille de calcul.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet23":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet23":::

### <a name="to-sort-data-in-a-listobject-control"></a>Pour trier les données d'un contrôle ListObject

1. Appelez la méthode <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> de la propriété <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> du contrôle Excel <xref:Microsoft.Office.Interop.Excel.ListObject> natif. L'exemple suivant suppose que vous disposez d'un contrôle Excel <xref:Microsoft.Office.Interop.Excel.ListObject> natif nommé `fruitList` dans la feuille de calcul active.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet24":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet24":::

## <a name="see-also"></a>Voir aussi
- [Utiliser des feuilles de calcul](../vsto/working-with-worksheets.md)
- [Comment : remplir automatiquement des plages par programmation avec des données à modification incrémentielle](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)
- [Comment : faire référence aux plages de la feuille de calcul dans le code par programmation](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Comment : appliquer des styles à des plages dans des classeurs par programmation](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [NamedRange, contrôle](../vsto/namedrange-control.md)
- [ListObject (contrôle)](../vsto/listobject-control.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
