---
title: Copier les données et la mise en forme dans les feuilles de calcul par programmation
description: Découvrez comment vous pouvez copier des données à partir d’une plage d’une feuille vers toutes les autres feuilles d’un classeur à l’aide de la méthode FillAcrossSheets.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying data
- formatting [Office development in Visual Studio]
- data [Office development in Visual Studio], copying across worksheets
- copying data, Office development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0696c99e78ee1b6a7acd174e5463bbdc514fe160
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828564"
---
# <a name="how-to-programmatically-copy-data-and-formatting-across-worksheets"></a>Comment : copier des données et la mise en forme par programmation dans des feuilles de calcul
  Vous pouvez copier des données à partir d’une plage d’une feuille vers toutes les autres feuilles d’un classeur à l’aide de la <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A> méthode. Spécifiez une plage et indiquez si vous souhaitez copier des données, une mise en forme ou les deux.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>Exemple
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet44":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet44":::

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple requiert une plage nommée `rangeData` dans une feuille de calcul.

## <a name="see-also"></a>Voir aussi
- [Utiliser des feuilles de calcul](../vsto/working-with-worksheets.md)
- [Comment : ajouter des feuilles de calcul à des classeurs par programmation](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Comment : modifier la mise en forme des lignes de feuille de calcul contenant des cellules sélectionnées par programmation](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
