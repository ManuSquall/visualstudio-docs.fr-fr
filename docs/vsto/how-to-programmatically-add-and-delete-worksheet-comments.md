---
title: 'Comment : ajouter et supprimer des commentaires de feuille de calcul par programmation'
description: Découvrez comment vous pouvez ajouter et supprimer des commentaires par programmation dans Microsoft Office des feuilles de calcul Excel. Vous pouvez uniquement ajouter des commentaires à des cellules uniques, et non à des plages de cellules multiples.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, comments
- worksheets, comments
- comments, worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 20b718be3bec6cac3ee6c0b0985fa6efca867189
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826939"
---
# <a name="how-to-programmatically-add-and-delete-worksheet-comments"></a>Comment : ajouter et supprimer des commentaires de feuille de calcul par programmation
  Vous pouvez ajouter et supprimer des commentaires dans des feuilles de calcul Microsoft Office Excel par programmation. Vous pouvez ajouter des commentaires uniquement à des cellules individuelles, et non à des plages de cellules.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="add-and-delete-a-comment-in-a-document-level-project"></a>Ajouter et supprimer un commentaire dans un projet au niveau du document
 Les exemples suivants partent du principe qu’il existe un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> à cellule unique nommé `dateComment` sur une feuille de calcul nommée `Sheet1`.

### <a name="to-add-a-new-comment-to-a-named-range"></a>Pour ajouter un nouveau commentaire à une plage nommée

1. Appelez la méthode <xref:Microsoft.Office.Tools.Excel.NamedRange.AddComment%2A> du contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> et spécifiez le texte du commentaire. Vous devez placer ce code dans la classe `Sheet1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet30":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet30":::

#### <a name="to-delete-a-comment-from-a-named-range"></a>Pour supprimer un commentaire d’une plage nommée

1. Vérifiez qu’il existe un commentaire sur la plage et supprimez-le. Vous devez placer ce code dans la classe `Sheet1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet29":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet29":::

## <a name="add-and-delete-a-comment-in-a-vsto-add-in-project"></a>Ajouter et supprimer un commentaire dans un projet de complément VSTO
 Les exemples suivants partent du principe qu’il existe un <xref:Microsoft.Office.Interop.Excel.Range> à cellule unique nommé `dateComment` sur la feuille de calcul active.

### <a name="to-add-a-new-comment-to-an-excel-range"></a>Pour ajouter un nouveau commentaire à une plage Excel

1. Appelez la méthode <xref:Microsoft.Office.Interop.Excel.Range.AddComment%2A> du <xref:Microsoft.Office.Interop.Excel.Range> et spécifiez le texte du commentaire.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet20":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet20":::

### <a name="to-delete-a-comment-from-an-excel-range"></a>Pour supprimer un commentaire d’une plage Excel

1. Vérifiez qu’il existe un commentaire sur la plage et supprimez-le.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet19":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet19":::

## <a name="see-also"></a>Voir aussi
- [Utiliser des feuilles de calcul](../vsto/working-with-worksheets.md)
- [Comment : afficher des commentaires de feuille de calcul par programmation](../vsto/how-to-programmatically-display-worksheet-comments.md)
- [NamedRange, contrôle](../vsto/namedrange-control.md)
