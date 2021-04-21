---
title: 'Comment : appliquer des styles à des plages dans des classeurs par programmation'
description: Découvrez comment vous pouvez appliquer des styles nommés à des zones dans les classeurs. Excel fournit différents styles prédéfinis.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, styles
- styles, workbook ranges
- workbooks, styles
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b1ce30c9a0e21bd4b8860f7a4d17191c48cd2ad9
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828304"
---
# <a name="how-to-programmatically-apply-styles-to-ranges-in-workbooks"></a>Comment : appliquer des styles à des plages dans des classeurs par programmation
  Vous pouvez appliquer des styles nommés à des zones dans les classeurs. Excel fournit différents styles prédéfinis.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 La boîte de dialogue **Format de cellule** affiche toutes les options que vous pouvez utiliser pour formater des cellules, et chacune de ces options est disponible à partir de votre code. Pour afficher cette boîte de dialogue dans Excel, cliquez sur **Cellules** dans le menu **Format** .

## <a name="to-apply-a-style-to-a-named-range-in-a-document-level-customization"></a>Pour appliquer un style à une plage nommée dans une personnalisation au niveau du document

1. Créez un style et définissez ses attributs.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet53":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet53":::

2. Créez un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange>, affectez-lui du texte, puis appliquez le nouveau style. Ce code doit être placé dans une classe Sheet et non pas dans la classe `ThisWorkbook` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet54":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet54":::

## <a name="to-clear-a-style-from-a-named-range-in-a-document-level-customization"></a>Pour supprimer un style d'une plage nommée dans une personnalisation au niveau du document

1. Appliquez le style Normal à la plage. Ce code doit être placé dans une classe Sheet et non pas dans la classe `ThisWorkbook` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet55":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet55":::

## <a name="to-apply-a-style-to-a-named-range-in-a-vsto-add-in"></a>Pour appliquer un style à une plage nommée dans un complément VSTO

1. Créez un style et définissez ses attributs.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet28":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet28":::

2. Créez <xref:Microsoft.Office.Interop.Excel.Range>, affectez-lui du texte, puis appliquez le nouveau style.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet29":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet29":::

## <a name="to-clear-a-style-from-a-named-range-in-a-vsto-add-in"></a>Pour effacer un style d’une plage nommée dans un complément VSTO

1. Appliquez le style Normal à la plage.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet56":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet56":::

## <a name="see-also"></a>Voir aussi
- [Utiliser des plages](../vsto/working-with-ranges.md)
- [NamedRange, contrôle](../vsto/namedrange-control.md)
- [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
