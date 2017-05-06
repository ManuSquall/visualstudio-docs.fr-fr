---
title: "Comment&#160;: ex&#233;cuter des calculs Excel par programmation"
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
  - "calculs, exécuter dans Excel"
  - "Excel (développement Office dans Visual Studio), exécuter des calculs par programmation"
  - "plages, exécuter des calculs"
  - "classeurs, exécuter des calculs"
ms.assetid: 0bf30d93-8620-43ad-bfb8-f45bf3b5461f
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Comment&#160;: ex&#233;cuter des calculs Excel par programmation
  Vous utilisez un processus semblable pour exécuter des calculs dans un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> ou un objet de plage Excel natif.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Exécution de calculs dans un contrôle NamedRange  
 L'exemple suivant crée un <xref:Microsoft.Office.Tools.Excel.NamedRange> à la cellule A1, puis calcule cette cellule.  Ce code doit être placé dans une classe sheet et non dans la classe `ThisWorkbook`.  
  
#### Pour exécuter des calculs dans un contrôle NamedRange  
  
1.  Créez la plage nommée.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#75](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#75)]
     [!code-vb[Trin_VstcoreExcelAutomation#75](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#75)]  
  
2.  Appelez la méthode <xref:Microsoft.Office.Tools.Excel.NamedRange.Calculate%2A> de la plage spécifiée.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#76](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#76)]
     [!code-vb[Trin_VstcoreExcelAutomation#76](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#76)]  
  
## Exécution de calculs dans une plage Excel native  
  
#### Pour exécuter des calculs dans une plage Excel native  
  
1.  Créez la plage nommée.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#30](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#30](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#30)]  
  
2.  Appelez la méthode <xref:Microsoft.Office.Interop.Excel.Range.Calculate%2A> de la plage spécifiée.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#31](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#31](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#31)]  
  
## Voir aussi  
 [Utilisation des plages](../vsto/working-with-ranges.md)   
 [NamedRange, contrôle](../vsto/namedrange-control.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  