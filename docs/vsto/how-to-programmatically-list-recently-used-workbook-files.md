---
title: 'Comment : répertorier les fichiers de classeur récemment utilisés par programmation'
description: Découvrez comment vous pouvez répertorier par programme les fichiers de classeur Microsoft Excel récemment utilisés à l’aide de Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ba7ca717af4330e8fb3c102b3a5fe5bf7d9162b6
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825327"
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>Comment : répertorier les fichiers de classeur récemment utilisés par programmation
  La <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> propriété retourne une collection qui contient les noms de tous les fichiers qui apparaissent dans la Microsoft Office liste Excel des fichiers récemment utilisés. La longueur de la liste varie selon le nombre de fichiers que l’utilisateur a sélectionnés à conserver. Vous pouvez afficher les résultats dans une plage.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Pour répertorier les classeurs récemment utilisés dans un objet Range

1. Parcourez la liste des fichiers récents et affichez les noms dans les cellules relatives à un <xref:Microsoft.Office.Interop.Excel.Range> objet.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet9":::

## <a name="see-also"></a>Voir aussi
- [Utiliser des classeurs](../vsto/working-with-workbooks.md)
- [NamedRange, contrôle](../vsto/namedrange-control.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
