---
title: 'Comment : copier par programmation les données et la mise en forme des feuilles de calcul | Documents Microsoft'
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
ms.openlocfilehash: 10a710af8120ab789ec3a9c3ccb2b7e4398e82f3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-copy-data-and-formatting-across-worksheets"></a>Comment : copier des données et une mise en forme d'une feuille de calcul à l'autre par programmation
  Vous pouvez copier des données à partir d’une plage d’une feuille à toutes les autres feuilles dans un classeur à l’aide de la <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A> (méthode). Spécifiez une plage, et si vous souhaitez copier des données, la mise en forme ou les deux.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="example"></a>Exemple  
 [!code-csharp[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#44)]
 [!code-vb[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#44)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple requiert une plage nommée `rangeData` dans une feuille de calcul.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des feuilles de calcul](../vsto/working-with-worksheets.md)   
 [Comment : ajouter par programmation des feuilles de calcul à des classeurs](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Comment : modifier par programmation la mise en forme dans les lignes de feuille de calcul contenant des cellules sélectionnées](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  