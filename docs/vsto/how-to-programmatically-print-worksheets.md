---
title: "Comment&#160;: imprimer des feuilles de calcul par programmation"
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
  - "aperçu avant impression, feuilles de calcul"
  - "imprimer (développement Office dans Visual Studio), feuilles de calcul"
  - "feuilles de calcul, imprimer"
ms.assetid: 312bfcd7-0a74-421c-b42e-df71a06b7bdf
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# Comment&#160;: imprimer des feuilles de calcul par programmation
  Vous pouvez imprimer une feuille de calcul dans un classeur.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Impression d'une feuille de calcul dans une personnalisation au niveau du document  
  
#### Pour imprimer une feuille de calcul  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintOut%2A> de `Sheet1`, demandez deux exemplaires et prévisualisez le document avant l'impression.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#22](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#22)]
     [!code-vb[Trin_VstcoreExcelAutomation#22](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#22)]  
  
 La méthode <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> vous permet d'afficher l'objet spécifié dans la fenêtre **Aperçu avant impression**.  Le code suivant suppose que vous ayez un élément hôte <xref:Microsoft.Office.Tools.Excel.Worksheet> nommé `Sheet1`.  
  
#### Pour afficher une page avant l'impression  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> de la feuille de calcul.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#23](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomation#23](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#23)]  
  
## Impression d'une feuille de calcul dans un complément VSTO  
  
#### Pour imprimer une feuille de calcul  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A> de la feuille de calcul active, demandez deux exemplaires et prévisualisez le document avant l'impression.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#14)]  
  
 La méthode <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> vous permet d'afficher l'objet spécifié dans la fenêtre **Aperçu avant impression**.  
  
#### Pour afficher une page avant l'impression  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> de la feuille de calcul active.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#15)]  
  
## Voir aussi  
 [Utilisation des feuilles de calcul](../vsto/working-with-worksheets.md)   
 [Comment : vérifier l'orthographe dans les feuilles de calcul par programmation](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [Élément hôte de feuille de calcul](../vsto/worksheet-host-item.md)   
 [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  