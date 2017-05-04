---
title: "Comment&#160;: r&#233;pertorier toutes les feuilles de calcul d&#39;un classeur par programmation | Microsoft Docs"
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
  - "classeurs, répertorier les feuilles de calcul"
  - "feuilles de calcul, répertorier"
ms.assetid: 38b63d1d-6047-44e8-b089-c576c6179e4a
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# Comment&#160;: r&#233;pertorier toutes les feuilles de calcul d&#39;un classeur par programmation
  La classe <xref:Microsoft.Office.Interop.Excel.Workbook> fournit un objet <xref:Microsoft.Office.Interop.Excel.Worksheets>.  Cet objet contient une collection de tous les objets <xref:Microsoft.Office.Interop.Excel.Worksheet> du classeur spécifié.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### Pour répertorier toutes les feuilles de calcul existantes dans un classeur dans une personnalisation au niveau du document  
  
1.  Itérez au sein de la collection <xref:Microsoft.Office.Interop.Excel.Worksheets> et envoyez le nom de chaque feuille vers une cellule décalée par un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomation#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#21)]  
  
### Pour répertorier toutes les feuilles de calcul existantes d'un classeur dans un complément VSTO  
  
1.  Itérez au sein de la collection <xref:Microsoft.Office.Interop.Excel.Worksheets> et envoyez le nom de chaque feuille vers une cellule décalée par un objet <xref:Microsoft.Office.Interop.Excel.Range>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#13)]  
  
## Voir aussi  
 [Utilisation des feuilles de calcul](../vsto/working-with-worksheets.md)   
 [Comment : ajouter des feuilles de calcul à des classeurs par programmation](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Comment : déplacer des feuilles de calcul dans les classeurs par programmation](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)  
  
  