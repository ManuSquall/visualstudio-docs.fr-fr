---
title: "Comment : afficher des commentaires de feuille de calcul par programmation | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, comments
- comments, worksheets
ms.assetid: f5ce5e7f-bae4-40b7-951c-0f15b140aaf2
caps.latest.revision: "43"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6a57d625fcb87f5e101cc1e0f60b79a74c132b8f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-display-worksheet-comments"></a>Comment : afficher des commentaires de feuille de calcul par programmation
  Vous pouvez afficher et masquer des commentaires dans des feuilles de calcul Microsoft Office Excel par programmation.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-display-all-comments-on-a-worksheet-in-a-document-level-customization"></a>Pour afficher tous les commentaires dans une feuille de calcul dans une personnalisation au niveau du document  
  
1.  Affectez à la propriété <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> la valeur **true** si vous souhaitez afficher les commentaires ; sinon, affectez-lui la valeur **false**. Ce code doit être placé dans une classe Sheet et non pas dans la classe `ThisWorkbook` .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#31)]  
  
### <a name="to-display-all-comments-on-a-worksheet-in-an-application-level-vsto-add-in"></a>Pour afficher tous les commentaires dans une feuille de calcul dans un complément VSTO de niveau application  
  
1.  Affectez à la propriété <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> la valeur **true** si vous souhaitez afficher les commentaires ; sinon, affectez-lui la valeur **false**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#21)]  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des feuilles de calcul](../vsto/working-with-worksheets.md)   
 [Comment : ajouter par programmation et de supprimer des commentaires de feuille de calcul](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)   
 [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)  
  
  