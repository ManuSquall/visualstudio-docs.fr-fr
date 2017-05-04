---
title: "Comment&#160;: prot&#233;ger des classeurs par programmation | Microsoft Docs"
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
  - "protection du document, ajouter à des classeurs"
  - "protection du document, supprimer dans des classeurs"
  - "documents (développement Office dans Visual Studio), protection du document"
  - "classeurs, mots de passe"
  - "classeurs, protéger"
  - "classeurs, déprotéger"
ms.assetid: 553c67b9-e2a4-46b6-878c-5b4b4efa4589
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Comment&#160;: prot&#233;ger des classeurs par programmation
  Vous pouvez protéger un classeur Microsoft Office Excel afin que les utilisateurs ne puissent pas ajouter ni supprimer des feuilles de calcul et également ôter la protection du classeur par programmation.  Vous pouvez éventuellement spécifier un mot de passe et indiquer si vous souhaitez que la structure soit protégée \(de manière à ce que les utilisateurs ne puissent pas déplacer les feuilles\) et que les fenêtres du classeur soient protégées.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 La protection d'un classeur n'empêche pas les utilisateurs de modifier les cellules.  Pour protéger les données, vous devez protéger les feuilles de calcul.  Pour plus d’informations, consultez [Comment : protéger des feuilles de calcul par programmation](../vsto/how-to-programmatically-protect-worksheets.md).  
  
 Les exemples de code suivants utilisent une variable contenant un mot de passe fourni par l'utilisateur.  
  
## Protection d'un classeur faisant partie d'une personnalisation au niveau du document  
  
#### Pour protéger un classeur  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> du classeur et ajoutez un mot de passe.  Pour utiliser l'exemple de code suivant, exécutez\-le dans la classe `ThisWorkbook`, pas dans une classe de feuille.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#10)]
     [!code-vb[Trin_VstcoreExcelAutomation#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#10)]  
  
#### Pour ôter la protection d'un classeur  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A>, en passant un mot de passe s'il est requis.  Pour utiliser l'exemple de code suivant, exécutez\-le dans la classe `ThisWorkbook`, pas dans une classe de feuille.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomation#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#11)]  
  
## Protection d'un classeur à l'aide d'un complément d'application  
  
#### Pour protéger un classeur  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A> du classeur et ajoutez un mot de passe.  Cet exemple de code utilise le classeur actif.  Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisAddIn` de votre projet.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#6)]  
  
#### Pour ôter la protection d'un classeur  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A> du classeur actif, en passant un mot de passe s'il est requis.  Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisAddIn` de votre projet.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#7)]  
  
## Voir aussi  
 [Utilisation des classeurs](../vsto/working-with-workbooks.md)   
 [Comment : protéger des feuilles de calcul par programmation](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Comment : masquer des feuilles de calcul par programmation](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  