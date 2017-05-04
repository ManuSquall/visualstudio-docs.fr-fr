---
title: "Comment&#160;: ajouter des feuilles de calcul &#224; des classeurs par programmation | Microsoft Docs"
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
  - "classeurs, ajouter des feuilles de calcul"
  - "classeurs, créer des feuilles de calcul"
  - "feuilles de calcul, créer"
  - "feuilles de calcul, ajouter à des classeurs"
ms.assetid: 19f0d815-51b2-406c-9f36-34aa0ec16b4a
caps.latest.revision: 52
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 51
---
# Comment&#160;: ajouter des feuilles de calcul &#224; des classeurs par programmation
  Vous pouvez créer par programmation une feuille de calcul, puis ajouter la feuille de calcul à la collection de feuilles de calcul du classeur.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### Pour ajouter une nouvelle feuille de calcul à un classeur dans une personnalisation au niveau du document  
  
1.  Utilisez la méthode <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> de la collection <xref:Microsoft.Office.Interop.Excel.Sheets>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomation#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#15)]  
  
     La nouvelle feuille de calcul est un objet <xref:Microsoft.Office.Interop.Excel.Worksheet> natif et non un élément hôte. Si vous souhaitez ajouter un élément hôte <xref:Microsoft.Office.Tools.Excel.Worksheet>, vous devez ajouter la feuille de calcul au moment du design.  
  
### Pour ajouter une nouvelle feuille de calcul à un classeur dans un complément VSTO  
  
1.  Utilisez la méthode <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> de la collection <xref:Microsoft.Office.Interop.Excel.Sheets>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#11)]  
  
     La nouvelle feuille de calcul est un objet <xref:Microsoft.Office.Interop.Excel.Worksheet> natif et non un élément hôte. Vous pouvez également générer un élément hôte <xref:Microsoft.Office.Tools.Excel.Worksheet> à partir de l'objet <xref:Microsoft.Office.Interop.Excel.Worksheet> natif. Pour plus d'informations, consultez [Extension de documents Word et de classeurs Excel dans des compléments VSTO au moment de l'exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## Voir aussi  
 [Utilisation des feuilles de calcul](../vsto/working-with-worksheets.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Comment : supprimer des feuilles de calcul des classeurs par programmation](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Comment : sélectionner des feuilles de calcul par programmation](../vsto/how-to-programmatically-select-worksheets.md)   
 [Automatisation d'Excel à l'aide d'objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  