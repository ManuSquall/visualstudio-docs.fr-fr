---
title: "Comment&#160;: ajouter et supprimer des commentaires de feuille de calcul par programmation"
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
  - "plages, commentaires"
  - "feuilles de calcul, commentaires"
  - "commentaires, feuilles de calcul"
ms.assetid: 3408ce22-a7b7-4e2b-bfc1-dc24d679ee73
caps.latest.revision: 53
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# Comment&#160;: ajouter et supprimer des commentaires de feuille de calcul par programmation
  Vous pouvez ajouter et supprimer des commentaires dans des feuilles de calcul Microsoft Office Excel par programmation. Vous pouvez ajouter des commentaires uniquement à des cellules individuelles, et non à des plages de cellules.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Ajout et suppression d’un commentaire dans un projet au niveau du document  
 Les exemples suivants partent du principe qu’il existe un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> à cellule unique nommé `dateComment` sur une feuille de calcul nommée `Sheet1`.  
  
#### Pour ajouter un nouveau commentaire à une plage nommée  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Excel.NamedRange.AddComment%2A> du contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> et spécifiez le texte du commentaire. Vous devez placer ce code dans la classe `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#30](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomation#30](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#30)]  
  
#### Pour supprimer un commentaire d’une plage nommée  
  
1.  Vérifiez qu’il existe un commentaire sur la plage et supprimez\-le. Vous devez placer ce code dans la classe `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#29](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomation#29](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#29)]  
  
## Ajout et suppression d’un commentaire dans un projet de complément VSTO  
 Les exemples suivants partent du principe qu’il existe un <xref:Microsoft.Office.Interop.Excel.Range> à cellule unique nommé `dateComment` sur la feuille de calcul active.  
  
#### Pour ajouter un nouveau commentaire à une plage Excel  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Excel.Range.AddComment%2A> du <xref:Microsoft.Office.Interop.Excel.Range> et spécifiez le texte du commentaire.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#20)]  
  
#### Pour supprimer un commentaire d’une plage Excel  
  
1.  Vérifiez qu’il existe un commentaire sur la plage et supprimez\-le.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#19)]  
  
## Voir aussi  
 [Utilisation des feuilles de calcul](../vsto/working-with-worksheets.md)   
 [Comment : afficher des commentaires de feuille de calcul par programmation](../vsto/how-to-programmatically-display-worksheet-comments.md)   
 [NamedRange, contrôle](../vsto/namedrange-control.md)  
  
  