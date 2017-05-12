---
title: "Comment&#160;: ouvrir des classeurs par programmation"
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
  - "Excel (développement Office dans Visual Studio), ouvrir des classeurs"
  - "classeurs, ouvrir"
ms.assetid: 06c0ac87-a2c6-4cc1-87be-39be0cb81c71
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# Comment&#160;: ouvrir des classeurs par programmation
  La collection <xref:Microsoft.Office.Interop.Excel.Workbooks> de Microsoft Office Excel permet d'utiliser tous les classeurs ouverts et d'ouvrir des classeurs.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### Pour ouvrir un classeur existant  
  
1.  Utilisez la méthode <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> de la collection <xref:Microsoft.Office.Interop.Excel.Workbooks>, en passant le chemin d'accès au classeur.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#2)]  
  
## Compilation du code  
 Cet exemple de code nécessite ce qui suit :  
  
-   Un classeur nommé `YourWorkbook.xls` doit résider dans un répertoire nommé `Test` sur le lecteur C.  
  
## Voir aussi  
 [Utilisation des classeurs](../vsto/working-with-workbooks.md)   
 [Comment : ouvrir des fichiers texte en tant que classeurs par programmation](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)   
 [Comment : créer des classeurs par programmation](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [Comment : enregistrer des classeurs par programmation](../vsto/how-to-programmatically-save-workbooks.md)   
 [Comment : fermer des classeurs par programmation](../vsto/how-to-programmatically-close-workbooks.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)  
  
  