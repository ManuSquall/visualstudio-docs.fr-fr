---
title: "Comment&#160;: masquer des feuilles de calcul par programmation"
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
  - "feuilles de calcul masquées"
  - "feuilles de calcul, masquer"
ms.assetid: 3208f633-137f-47f9-9c9c-2cf8e3c72096
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Comment&#160;: masquer des feuilles de calcul par programmation
  Vous pouvez afficher ou masquer une feuille de calcul dans un classeur. Pour masquer une feuille de calcul, utilisez l’élément hôte de feuille de calcul ou accédez à la feuille de calcul à l’aide de la collection Sheets du classeur.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Utilisation de l'élément hôte de feuille de calcul  
 Si la feuille de calcul a été ajoutée au moment du design dans une personnalisation au niveau du document, utilisez la propriété <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> pour masquer la feuille de calcul spécifiée.  
  
#### Pour masquer une feuille de calcul à l’aide d’un élément hôte de feuille de calcul  
  
1.  Affectez à la propriété <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> de l’élément hôte `Sheet1` la valeur d’énumération <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomation#25](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#25)]  
  
## Utilisation de la collection Sheets du classeur Excel  
 Accédez aux feuilles de calcul via la collection <xref:Microsoft.Office.Interop.Excel.Sheets> Microsoft Office Excel dans les cas suivants :  
  
-   Vous souhaitez masquer une feuille de calcul dans un complément VSTO.  
  
-   La feuille de calcul à masquer a été créée au moment de l’exécution dans une personnalisation au niveau du document.  
  
#### Pour masquer une feuille de calcul à l’aide de la collection Sheets du classeur Excel  
  
1.  Affectez à la propriété <xref:Microsoft.Office.Interop.Excel.Worksheets.Visible%2A> de la feuille de calcul la valeur d’énumération <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomation#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#26)]  
  
## Voir aussi  
 [Utilisation des feuilles de calcul](../vsto/working-with-worksheets.md)   
 [Comment : supprimer des feuilles de calcul des classeurs par programmation](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Comment : déplacer des feuilles de calcul dans les classeurs par programmation](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [Comment : protéger des feuilles de calcul par programmation](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)  
  
  