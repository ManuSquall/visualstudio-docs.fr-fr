---
title: "Comment&#160;: afficher des commentaires de feuille de calcul par programmation"
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
  - "feuilles de calcul, commentaires"
  - "commentaires, feuilles de calcul"
ms.assetid: f5ce5e7f-bae4-40b7-951c-0f15b140aaf2
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Comment&#160;: afficher des commentaires de feuille de calcul par programmation
  Vous pouvez afficher et masquer des commentaires dans des feuilles de calcul Microsoft Office Excel par programmation.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### Pour afficher tous les commentaires dans une feuille de calcul dans une personnalisation au niveau du document  
  
1.  Affectez à la propriété <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> la valeur **true** si vous souhaitez afficher les commentaires ; sinon, affectez\-lui la valeur **false**. Ce code doit être placé dans une classe Sheet et non pas dans la classe `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#31](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomation#31](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#31)]  
  
### Pour afficher tous les commentaires dans une feuille de calcul dans un complément VSTO de niveau application  
  
1.  Affectez à la propriété <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> la valeur **true** si vous souhaitez afficher les commentaires ; sinon, affectez\-lui la valeur **false**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#21)]  
  
## Voir aussi  
 [Utilisation des feuilles de calcul](../vsto/working-with-worksheets.md)   
 [Comment : ajouter et supprimer des commentaires de feuille de calcul par programmation](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)  
  
  