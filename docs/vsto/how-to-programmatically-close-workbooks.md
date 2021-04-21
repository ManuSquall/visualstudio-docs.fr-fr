---
title: 'Comment : fermer des classeurs par programmation'
description: Découvrez comment vous pouvez fermer le classeur actif ou spécifier un classeur à fermer par programmation.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, closing
- Excel [Office development in Visual Studio], closing workbooks
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d09cbff06b1bb7048316629b7b958ee299029ec8
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825262"
---
# <a name="how-to-programmatically-close-workbooks"></a>Comment : fermer des classeurs par programmation
  Vous pouvez fermer le classeur actif ou spécifier un classeur à fermer.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="close-the-active-workbook"></a>Fermer le classeur actif
 Deux procédures permettent de fermer le classeur actif : une pour les personnalisations au niveau du document et une autre pour les compléments VSTO.

### <a name="to-close-the-active-workbook-in-a-document-level-customization"></a>Pour fermer le classeur actif dans une personnalisation au niveau du document

1. Appelez la méthode <xref:Microsoft.Office.Tools.Excel.Workbook.Close%2A> pour fermer le classeur associé à la personnalisation. Pour utiliser l'exemple de code suivant, exécutez-le dans la classe `Sheet1` d'un projet au niveau du document pour Excel.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet3":::

### <a name="to-close-the-active-workbook-in-a-vsto-add-in"></a>Pour fermer le classeur actif dans un complément VSTO

1. Appelez la méthode <xref:Microsoft.Office.Interop.Excel._Workbook.Close%2A> pour fermer le classeur actif. Pour utiliser l’exemple de code suivant, exécutez-le dans la classe `ThisAddIn` dans un projet de complément VSTO pour Excel.

:::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet1":::
:::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet1":::

## <a name="close-a-workbook-that-you-specify-by-name"></a>Fermer un classeur dont vous spécifiez le nom
 Pour fermer un classeur dont vous spécifiez le nom, vous devez procéder de la même manière que pour les compléments VSTO et les personnalisations au niveau du document.

### <a name="to-close-a-workbook-that-you-specify-by-name"></a>Pour fermer un classeur dont vous spécifiez le nom

1. Spécifiez le nom du classeur en tant qu'argument de la collection <xref:Microsoft.Office.Interop.Excel.Workbooks> . L’exemple de code suivant suppose qu’un classeur nommé **NewWorkbook** est ouvert dans Excel.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet2":::

## <a name="see-also"></a>Voir aussi
- [Utiliser des classeurs](../vsto/working-with-workbooks.md)
- [Comment : enregistrer des classeurs par programmation](../vsto/how-to-programmatically-save-workbooks.md)
- [Comment : ouvrir des classeurs par programmation](../vsto/how-to-programmatically-open-workbooks.md)
- [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
- [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
