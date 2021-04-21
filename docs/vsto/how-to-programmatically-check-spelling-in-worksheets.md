---
title: 'Comment : vérifier l’orthographe dans les feuilles de calcul par programmation'
description: Découvrez comment vous pouvez vérifier par programmation l’orthographe des mots dans une feuille de calcul Microsoft Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- spellchecking
- spelling checker, worksheets
- worksheets, checking spelling
- spelling, checking in worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1bf35e225def686ae2424a89b7e5d6b77207ccee
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826055"
---
# <a name="how-to-programmatically-check-spelling-in-worksheets"></a>Comment : vérifier l’orthographe dans les feuilles de calcul par programmation
  Vous pouvez vérifier par programmation l’orthographe des mots contenus dans une feuille de calcul. La boîte de dialogue **Orthographe** s’affiche automatiquement si des mots mal orthographiés figurent dans la feuille de calcul.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-check-spelling-in-a-worksheet-in-a-document-level-customization"></a>Pour vérifier l’orthographe d’une feuille de calcul dans une personnalisation au niveau du document

1. Appelez la méthode <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> de la feuille de calcul.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet45":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet45":::

## <a name="to-check-spelling-in-a-worksheet-in-a-vsto-add-in"></a>Pour vérifier l’orthographe d’une feuille de calcul dans un complément VSTO

1. Appelez la méthode <xref:Microsoft.Office.Interop.Excel._Worksheet.CheckSpelling%2A> de la feuille de calcul active.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet22":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet22":::

## <a name="see-also"></a>Voir aussi
- [Utiliser des feuilles de calcul](../vsto/working-with-worksheets.md)
- [Comment : exécuter des calculs Excel par programmation](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [NamedRange, contrôle](../vsto/namedrange-control.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
