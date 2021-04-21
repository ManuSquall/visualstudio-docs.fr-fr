---
title: 'Comment : Rechercher du texte dans les plages de la feuille de calcul par programmation'
description: Découvrez comment vous pouvez utiliser Visual Studio pour rechercher du texte dans les plages de feuille de calcul Microsoft Excel par programmation.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, searching
- text [Office development in Visual Studio], searching in worksheets
- text searches, worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 762cb3fc35b43bfd3ad15aea669adff2d370b632
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827940"
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>Comment : Rechercher du texte dans les plages de la feuille de calcul par programmation
  La <xref:Microsoft.Office.Interop.Excel.Range.Find%2A> méthode de l' <xref:Microsoft.Office.Interop.Excel.Range> objet vous permet de rechercher du texte dans la plage. Ce texte peut également être l’une des chaînes d’erreur qui peuvent s’afficher dans une cellule de feuille de calcul telle que `#NULL!` ou `#VALUE!` . Pour plus d’informations sur les chaînes d’erreur, consultez [valeurs d’erreur de cellule](/office/vba/excel/Concepts/Cells-and-Ranges/cell-error-values).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 L’exemple suivant recherche dans une plage nommée `Fruits` et modifie la police des cellules qui contiennent le mot « apples ». Cette procédure utilise également la <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> méthode, qui utilise les paramètres de recherche précédemment définis pour répéter la recherche. Vous spécifiez la cellule après laquelle effectuer la recherche, et la <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> méthode gère le reste.

> [!NOTE]
> La <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> recherche de la méthode revient au début de la plage de recherche après qu’elle a atteint la fin de la plage. Votre code doit vérifier que la recherche n’est pas entourée dans une boucle infinie. L’exemple de procédure illustre une manière de gérer cela à l’aide de la <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> propriété.

## <a name="to-search-for-text-in-a-worksheet-range"></a>Pour rechercher du texte dans une plage de feuille de calcul

1. Déclarez les variables pour le suivi de la plage entière, de la première plage trouvée et de la plage trouvée en cours.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet58":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet58":::

2. Recherchez la première correspondance, en spécifiant tous les paramètres à l’exception de la cellule dans laquelle effectuer la recherche.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet59":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet59":::

3. Poursuivez la recherche tant qu’il y a des correspondances.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet60":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet60":::

4. Comparez la première plage trouvée ( `firstFind` ) à **rien**. Si `firstFind` ne contient aucune valeur, le code stocke la plage trouvée ( `currentFind` ).

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet61":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet61":::

5. Quittez la boucle si l’adresse de la plage trouvée correspond à l’adresse de la première plage trouvée.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet62":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet62":::

6. Définissez l’apparence de la plage trouvée.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet63":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet63":::

7. Effectuez une autre recherche.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet64":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet64":::

   L'exemple suivant montre la méthode complète.

## <a name="example"></a>Exemple
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet57":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet57":::

## <a name="see-also"></a>Voir aussi
- [Utiliser des plages](../vsto/working-with-ranges.md)
- [Comment : appliquer des styles à des plages dans des classeurs par programmation](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Comment : faire référence aux plages de la feuille de calcul dans le code par programmation](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
