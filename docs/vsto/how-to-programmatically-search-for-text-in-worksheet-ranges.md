---
title: 'Comment : Rechercher du texte dans les plages de la feuille de calcul par programmation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, searching
- text [Office development in Visual Studio], searching in worksheets
- text searches, worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0ffc06c2f50f7a304ef76ac1451ee47419143afb
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985822"
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>Comment : Rechercher du texte dans les plages de la feuille de calcul par programmation
  La méthode <xref:Microsoft.Office.Interop.Excel.Range.Find%2A> de l’objet <xref:Microsoft.Office.Interop.Excel.Range> vous permet de rechercher du texte dans la plage. Ce texte peut également être l’une des chaînes d’erreur qui peuvent s’afficher dans une cellule de feuille de calcul telle que `#NULL!` ou `#VALUE!`. Pour plus d’informations sur les chaînes d’erreur, consultez [valeurs d’erreur de cellule](/office/vba/excel/Concepts/Cells-and-Ranges/cell-error-values).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 L’exemple suivant recherche une plage nommée `Fruits` et modifie la police des cellules qui contiennent le mot « apples ». Cette procédure utilise également la méthode <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>, qui utilise les paramètres de recherche précédemment définis pour répéter la recherche. Vous spécifiez la cellule après laquelle effectuer la recherche, et la méthode <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> gère le reste.

> [!NOTE]
> La recherche de la méthode <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> revient au début de la plage de recherche après qu’elle a atteint la fin de la plage. Votre code doit vérifier que la recherche n’est pas entourée dans une boucle infinie. L’exemple de procédure illustre une manière de gérer cela à l’aide de la propriété <xref:Microsoft.Office.Interop.Excel.Range.Address%2A>.

## <a name="to-search-for-text-in-a-worksheet-range"></a>Pour rechercher du texte dans une plage de feuille de calcul

1. Déclarez les variables pour le suivi de la plage entière, de la première plage trouvée et de la plage trouvée en cours.

    [!code-csharp[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#58)]
    [!code-vb[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#58)]

2. Recherchez la première correspondance, en spécifiant tous les paramètres à l’exception de la cellule dans laquelle effectuer la recherche.

    [!code-csharp[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#59)]
    [!code-vb[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#59)]

3. Poursuivez la recherche tant qu’il y a des correspondances.

    [!code-csharp[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#60)]
    [!code-vb[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#60)]

4. Comparez la première plage trouvée (`firstFind`) à **rien**. Si `firstFind` ne contient aucune valeur, le code stocke la plage trouvée (`currentFind`).

    [!code-csharp[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#61)]
    [!code-vb[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#61)]

5. Quittez la boucle si l’adresse de la plage trouvée correspond à l’adresse de la première plage trouvée.

    [!code-csharp[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#62)]
    [!code-vb[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#62)]

6. Définissez l’apparence de la plage trouvée.

    [!code-csharp[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#63)]
    [!code-vb[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#63)]

7. Effectuez une autre recherche.

    [!code-csharp[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#64)]
    [!code-vb[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#64)]

   L'exemple suivant montre la méthode complète.

## <a name="example"></a>Exemple
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#57)]

## <a name="see-also"></a>Voir aussi
- [Utiliser des plages](../vsto/working-with-ranges.md)
- [Comment : appliquer des styles à des plages dans des classeurs par programmation](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Comment : faire référence aux plages de la feuille de calcul dans le code par programmation](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
