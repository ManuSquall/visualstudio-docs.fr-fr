---
title: "Comment&#160;: fermer des classeurs par programmation"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "classeurs, fermeture"
  - "Excel (développement Office dans Visual Studio), fermeture de classeurs"
ms.assetid: 50709caf-2ad8-4843-987c-9a34c8c1e4fe
caps.latest.revision: 52
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 51
---
# Comment&#160;: fermer des classeurs par programmation
  Vous pouvez fermer le classeur actif ou spécifier un classeur à fermer.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Fermeture du classeur actif  
 Deux procédures permettent de fermer le classeur actif : une pour les personnalisations au niveau du document et une autre pour les compléments VSTO.  
  
#### Pour fermer le classeur actif dans une personnalisation au niveau du document  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Excel.Workbook.Close%2A> pour fermer le classeur associé à la personnalisation. Pour utiliser l'exemple de code suivant, exécutez\-le dans la classe `Sheet1` d'un projet au niveau du document pour Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomation#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#3)]  
  
#### Pour fermer le classeur actif dans un complément VSTO  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Excel._Workbook.Close%2A> pour fermer le classeur actif. Pour utiliser l’exemple de code suivant, exécutez\-le dans la classe `ThisAddIn` dans un projet de complément VSTO pour Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#1)]  
  
## Fermeture d'un classeur dont vous spécifiez le nom  
 Pour fermer un classeur dont vous spécifiez le nom, vous devez procéder de la même manière que pour les compléments VSTO et les personnalisations au niveau du document.  
  
#### Pour fermer un classeur dont vous spécifiez le nom  
  
1.  Spécifiez le nom du classeur en tant qu'argument de la collection <xref:Microsoft.Office.Interop.Excel.Workbooks>. L’exemple de code suivant suppose qu’un classeur nommé **NewWorkbook** est ouvert dans Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#2)]  
  
## Voir aussi  
 [Utilisation des classeurs](../vsto/working-with-workbooks.md)   
 [Comment : enregistrer des classeurs par programmation](../vsto/how-to-programmatically-save-workbooks.md)   
 [Comment : ouvrir des classeurs par programmation](../vsto/how-to-programmatically-open-workbooks.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)  
  
  