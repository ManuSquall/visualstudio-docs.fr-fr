---
title: 'Comment : répertorier les fichiers de classeur récemment utilisés par programmation'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, listing recently used
- RecentFiles property
- Excel [Office development in Visual Studio], recently used files listing
- recent file list, Excel
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4f4f34a8ed848d548b2e23d3f9a3cf3c603c7cad
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85541360"
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>Comment : répertorier les fichiers de classeur récemment utilisés par programmation
  La <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> propriété retourne une collection qui contient les noms de tous les fichiers qui apparaissent dans la Microsoft Office liste Excel des fichiers récemment utilisés. La longueur de la liste varie selon le nombre de fichiers que l’utilisateur a sélectionnés à conserver. Vous pouvez afficher les résultats dans une plage.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Pour répertorier les classeurs récemment utilisés dans un objet Range

1. Parcourez la liste des fichiers récents et affichez les noms dans les cellules relatives à un <xref:Microsoft.Office.Interop.Excel.Range> objet.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]

## <a name="see-also"></a>Voir aussi
- [Utiliser des classeurs](../vsto/working-with-workbooks.md)
- [NamedRange, contrôle](../vsto/namedrange-control.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
