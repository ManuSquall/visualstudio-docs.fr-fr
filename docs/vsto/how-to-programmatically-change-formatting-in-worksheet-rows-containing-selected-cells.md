---
title: Modifier les formats des lignes contenant des cellules sélectionnées par le biais du code
description: Découvrez comment vous pouvez modifier la police d’une ligne entière qui contient une cellule sélectionnée afin que le texte soit gras.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- rows [Office development in Visual Studio]
- formatting [Office development in Visual Studio]
- worksheets, changing formatting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 62b9f94bfa423b149fef6abb984a03536d0e3d8c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875313"
---
# <a name="how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells"></a>Comment : modifier la mise en forme des lignes de feuille de calcul contenant des cellules sélectionnées par programmation
  Vous pouvez modifier la police d’une ligne entière qui contient une cellule sélectionnée afin que le texte soit gras.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-make-the-current-row-bold-and-the-previously-bolded-row-normal"></a>Pour mettre la ligne actuelle en gras et la ligne précédemment en gras normal

1. Déclarez une variable statique pour effectuer le suivi de la ligne sélectionnée précédemment.

    [!code-csharp[Trin_VstcoreExcelAutomation#37](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#37)]
    [!code-vb[Trin_VstcoreExcelAutomation#37](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#37)]

2. Récupérez une référence à la cellule active à l’aide de la <xref:Microsoft.Office.Interop.Excel._Application.ActiveCell%2A> propriété.

    [!code-csharp[Trin_VstcoreExcelAutomation#38](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#38)]
    [!code-vb[Trin_VstcoreExcelAutomation#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#38)]

3. Style de la ligne actuelle en gras à l’aide <xref:Microsoft.Office.Interop.Excel.Range.EntireRow%2A> de la propriété de la cellule active.

    [!code-csharp[Trin_VstcoreExcelAutomation#39](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#39)]
    [!code-vb[Trin_VstcoreExcelAutomation#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#39)]

4. Vérifiez que la valeur actuelle de `previousRow` n’est pas 0. 0 (zéro) indique qu’il s’agit de la première fois que ce code est utilisé.

    [!code-csharp[Trin_VstcoreExcelAutomation#40](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#40)]
    [!code-vb[Trin_VstcoreExcelAutomation#40](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#40)]

5. Vérifiez que la ligne actuelle est différente de la ligne précédente.

    [!code-csharp[Trin_VstcoreExcelAutomation#41](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#41)]
    [!code-vb[Trin_VstcoreExcelAutomation#41](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#41)]

6. Récupérez une référence à une plage qui représente la ligne précédemment sélectionnée et définissez cette ligne pour qu’elle ne soit pas en gras.

    [!code-csharp[Trin_VstcoreExcelAutomation#42](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#42)]
    [!code-vb[Trin_VstcoreExcelAutomation#42](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#42)]

7. Stocke la ligne actuelle afin qu’elle puisse devenir la ligne précédente lors de la passe suivante.

    [!code-csharp[Trin_VstcoreExcelAutomation#43](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#43)]
    [!code-vb[Trin_VstcoreExcelAutomation#43](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#43)]

   L'exemple suivant montre la méthode complète.

## <a name="example"></a>Exemple
 [!code-csharp[Trin_VstcoreExcelAutomation#36](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#36)]
 [!code-vb[Trin_VstcoreExcelAutomation#36](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#36)]

## <a name="see-also"></a>Voir aussi
- [Utiliser des feuilles de calcul](../vsto/working-with-worksheets.md)
- [Comment : appliquer des styles à des plages dans des classeurs par programmation](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Comment : copier des données et la mise en forme par programmation dans des feuilles de calcul](../vsto/how-to-programmatically-copy-data-and-formatting-across-worksheets.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
