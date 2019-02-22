---
title: 'Procédure : Modifier la mise en forme dans les lignes de feuille de calcul contenant des cellules sélectionnées par programmation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- rows [Office development in Visual Studio]
- formatting [Office development in Visual Studio]
- worksheets, changing formatting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 52b96ce077ed2f45c22679c1be798ae8b2197e0a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56644989"
---
# <a name="how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells"></a>Procédure : Modifier la mise en forme dans les lignes de feuille de calcul contenant des cellules sélectionnées par programmation
  Vous pouvez modifier la police d’une ligne entière qui contient une cellule sélectionnée afin que le texte est en gras.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-make-the-current-row-bold-and-the-previously-bolded-row-normal"></a>Pour afficher la ligne actuelle en gras et précédemment les lignes en gras normal

1. Déclarez une variable statique pour effectuer le suivi de la ligne précédemment sélectionnée.

    [!code-csharp[Trin_VstcoreExcelAutomation#37](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#37)]
    [!code-vb[Trin_VstcoreExcelAutomation#37](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#37)]

2. Récupérer une référence à la cellule en cours à l’aide du <xref:Microsoft.Office.Interop.Excel._Application.ActiveCell%2A> propriété.

    [!code-csharp[Trin_VstcoreExcelAutomation#38](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#38)]
    [!code-vb[Trin_VstcoreExcelAutomation#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#38)]

3. Style de l’actuelle ligne en gras à l’aide du <xref:Microsoft.Office.Interop.Excel.Range.EntireRow%2A> propriété de la cellule active.

    [!code-csharp[Trin_VstcoreExcelAutomation#39](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#39)]
    [!code-vb[Trin_VstcoreExcelAutomation#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#39)]

4. Vérifiez que la valeur actuelle de `previousRow` est pas égal à 0. 0 (zéro) indique qu’il s’agit de la première fois sur ce code.

    [!code-csharp[Trin_VstcoreExcelAutomation#40](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#40)]
    [!code-vb[Trin_VstcoreExcelAutomation#40](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#40)]

5. Vérifiez que la ligne actuelle est différente de la ligne précédente.

    [!code-csharp[Trin_VstcoreExcelAutomation#41](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#41)]
    [!code-vb[Trin_VstcoreExcelAutomation#41](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#41)]

6. Récupérez une référence à une plage qui représente la ligne qui a été précédemment sélectionnée, jeu de cette ligne ne soit ne pas en gras.

    [!code-csharp[Trin_VstcoreExcelAutomation#42](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#42)]
    [!code-vb[Trin_VstcoreExcelAutomation#42](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#42)]

7. Store la ligne actuelle afin qu’elle devienne la ligne précédente pour le test suivant.

    [!code-csharp[Trin_VstcoreExcelAutomation#43](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#43)]
    [!code-vb[Trin_VstcoreExcelAutomation#43](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#43)]

   L'exemple suivant montre la méthode complète.

## <a name="example"></a>Exemple
 [!code-csharp[Trin_VstcoreExcelAutomation#36](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#36)]
 [!code-vb[Trin_VstcoreExcelAutomation#36](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#36)]

## <a name="see-also"></a>Voir aussi
- [Travailler avec des feuilles de calcul](../vsto/working-with-worksheets.md)
- [Guide pratique pour Appliquer des styles à des plages dans les classeurs par programmation](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Guide pratique pour Copier des données et la mise en forme entre feuilles de calcul par programmation](../vsto/how-to-programmatically-copy-data-and-formatting-across-worksheets.md)
- [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
