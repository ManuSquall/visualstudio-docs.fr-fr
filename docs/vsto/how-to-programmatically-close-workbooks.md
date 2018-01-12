---
title: "Comment : fermer des classeurs par programmation | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, closing
- Excel [Office development in Visual Studio], closing workbooks
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 321a0e7b38a15cc40308f92b436e4f88fdbaf55d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-close-workbooks"></a>Comment : fermer des classeurs par programmation
  Vous pouvez fermer le classeur actif ou spécifier un classeur à fermer.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="closing-the-active-workbook"></a>Fermeture du classeur actif  
 Deux procédures permettent de fermer le classeur actif : une pour les personnalisations au niveau du document et une autre pour les compléments VSTO.  
  
#### <a name="to-close-the-active-workbook-in-a-document-level-customization"></a>Pour fermer le classeur actif dans une personnalisation au niveau du document  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Excel.Workbook.Close%2A> pour fermer le classeur associé à la personnalisation. Pour utiliser l'exemple de code suivant, exécutez-le dans la classe `Sheet1` d'un projet au niveau du document pour Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#3](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomation#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#3)]  
  
#### <a name="to-close-the-active-workbook-in-a-vsto-add-in"></a>Pour fermer le classeur actif dans un complément VSTO  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Excel._Workbook.Close%2A> pour fermer le classeur actif. Pour utiliser l’exemple de code suivant, exécutez-le dans la classe `ThisAddIn` dans un projet de complément VSTO pour Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#1)]  
  
## <a name="closing-a-workbook-that-you-specify-by-name"></a>Fermeture d'un classeur dont vous spécifiez le nom  
 Pour fermer un classeur dont vous spécifiez le nom, vous devez procéder de la même manière que pour les compléments VSTO et les personnalisations au niveau du document.  
  
#### <a name="to-close-a-workbook-that-you-specify-by-name"></a>Pour fermer un classeur dont vous spécifiez le nom  
  
1.  Spécifiez le nom du classeur en tant qu'argument de la collection <xref:Microsoft.Office.Interop.Excel.Workbooks> . L’exemple de code suivant suppose qu’un classeur nommé **NewWorkbook** est ouvert dans Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#2)]  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des classeurs](../vsto/working-with-workbooks.md)   
 [Comment : enregistrer des classeurs par programmation](../vsto/how-to-programmatically-save-workbooks.md)   
 [Comment : ouvrir des classeurs par programmation](../vsto/how-to-programmatically-open-workbooks.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Paramètres optionnels dans les Solutions Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)  
  
  