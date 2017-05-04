---
title: "Comment&#160;: &#244;ter la protection des feuilles de calcul par programmation | Microsoft Docs"
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
  - "feuilles de calcul, ôter la protection"
  - "documents (développement Office dans Visual Studio), protection des documents"
  - "protection de document, ôter des feuilles de calcul"
  - "Unprotect (méthode)"
ms.assetid: 034688d2-eda7-4b4a-bcc2-d0999ff879a4
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# Comment&#160;: &#244;ter la protection des feuilles de calcul par programmation
  Vous pouvez supprimer par programmation la protection d’une feuille de calcul Microsoft Office Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 L’exemple suivant utilise la variable `getPasswordFromUser`, qui contient un mot de passe fourni par l’utilisateur.  
  
### Pour ôter la protection d’une feuille de calcul dans une personnalisation au niveau du document  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A> de la feuille de calcul et passez le mot de passe, si nécessaire. Cet exemple suppose que vous utilisez une feuille de calcul nommée `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#28](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomation#28](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#28)]  
  
### Pour ôter la protection d’une feuille de calcul dans un complément VSTO  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A> de la feuille de calcul active et passez le mot de passe, si nécessaire.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#18)]  
  
## Voir aussi  
 [Utilisation des feuilles de calcul](../vsto/working-with-worksheets.md)   
 [Comment : protéger des feuilles de calcul par programmation](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Comment : protéger des classeurs par programmation](../vsto/how-to-programmatically-protect-workbooks.md)   
 [Comment : masquer des feuilles de calcul par programmation](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)  
  
  