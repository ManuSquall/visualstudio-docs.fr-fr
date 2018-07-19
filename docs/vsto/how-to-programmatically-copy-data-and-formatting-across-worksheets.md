---
title: 'Comment : copier des données et la mise en forme entre feuilles de calcul par programmation'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying data
- formatting [Office development in Visual Studio]
- data [Office development in Visual Studio], copying across worksheets
- copying data, Office development in Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4a4cce083bee8b57ff37276ae909799a9a6791d7
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256680"
---
# <a name="how-to-programmatically-copy-data-and-formatting-across-worksheets"></a>Comment : copier des données et la mise en forme entre feuilles de calcul par programmation
  Vous pouvez copier des données à partir d’une plage d’une feuille à toutes les autres feuilles dans un classeur à l’aide de la <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A> (méthode). Spécifier une plage, et si vous souhaitez copier des données, la mise en forme ou les deux.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="example"></a>Exemple  
 [!code-csharp[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#44)]
 [!code-vb[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#44)]  
  
## <a name="compile-the-code"></a>Compiler le code  
 Cet exemple requiert une plage nommée `rangeData` dans une feuille de calcul.  
  
## <a name="see-also"></a>Voir aussi  
 [Travailler avec des feuilles de calcul](../vsto/working-with-worksheets.md)   
 [Comment : ajouter par programmation des feuilles de calcul à des classeurs](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Comment : modifier la mise en forme dans les lignes de feuille de calcul contenant des cellules sélectionnées par programmation](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  