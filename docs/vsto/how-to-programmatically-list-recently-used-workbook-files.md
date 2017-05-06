---
title: "Comment&#160;: r&#233;pertorier les fichiers de classeur r&#233;cemment utilis&#233;s par programmation"
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
  - "Excel (développement Office dans Visual Studio), liste des fichiers récemment utilisés"
  - "liste des fichiers récents, Excel"
  - "RecentFiles (propriété)"
  - "classeurs, répertorier les derniers utilisés"
ms.assetid: 210a3753-4845-4875-b34a-a30d3a1299b3
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Comment&#160;: r&#233;pertorier les fichiers de classeur r&#233;cemment utilis&#233;s par programmation
  La propriété <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> retourne une collection contenant les noms de tous les fichiers qui apparaissent dans la liste Microsoft Office Excel des fichiers récemment utilisés.  La longueur de la liste varie en fonction du nombre de fichiers que l'utilisateur a choisi de conserver.  Vous pouvez afficher les résultats dans une plage.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### Pour répertorier les classeurs récemment utilisés dans un objet de plage  
  
1.  Parcourez la liste des fichiers récents et affichez les noms dans les cellules relatives à un objet <xref:Microsoft.Office.Interop.Excel.Range>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#9)]  
  
## Voir aussi  
 [Utilisation des classeurs](../vsto/working-with-workbooks.md)   
 [NamedRange, contrôle](../vsto/namedrange-control.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  