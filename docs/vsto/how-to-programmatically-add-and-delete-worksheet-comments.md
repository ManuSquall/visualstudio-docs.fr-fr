---
title: 'Comment : ajouter et supprimer des commentaires de feuille de calcul par programmation'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, comments
- worksheets, comments
- comments, worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fe41fe7f6370697335fa76b468e79e61d6e1269a
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35670793"
---
# <a name="how-to-programmatically-add-and-delete-worksheet-comments"></a>Comment : ajouter et supprimer des commentaires de feuille de calcul par programmation
  Vous pouvez ajouter et supprimer des commentaires dans des feuilles de calcul Microsoft Office Excel par programmation. Vous pouvez ajouter des commentaires uniquement à des cellules individuelles, et non à des plages de cellules.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="add-and-delete-a-comment-in-a-document-level-project"></a>Ajouter et supprimer un commentaire dans un projet au niveau du document  
 Les exemples suivants partent du principe qu’il existe un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> à cellule unique nommé `dateComment` sur une feuille de calcul nommée `Sheet1`.  
  
### <a name="to-add-a-new-comment-to-a-named-range"></a>Pour ajouter un nouveau commentaire à une plage nommée  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Excel.NamedRange.AddComment%2A> du contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> et spécifiez le texte du commentaire. Vous devez placer ce code dans la classe `Sheet1` .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#30)]  
  
#### <a name="to-delete-a-comment-from-a-named-range"></a>Pour supprimer un commentaire d’une plage nommée  
  
1.  Vérifiez qu’il existe un commentaire sur la plage et supprimez-le. Vous devez placer ce code dans la classe `Sheet1` .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#29)]  
  
## <a name="add-and-delete-a-comment-in-a-vsto-add-in-project"></a>Ajouter et supprimer un commentaire dans un projet de complément VSTO  
 Les exemples suivants partent du principe qu’il existe un <xref:Microsoft.Office.Interop.Excel.Range> à cellule unique nommé `dateComment` sur la feuille de calcul active.  
  
### <a name="to-add-a-new-comment-to-an-excel-range"></a>Pour ajouter un nouveau commentaire à une plage Excel  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Excel.Range.AddComment%2A> du <xref:Microsoft.Office.Interop.Excel.Range> et spécifiez le texte du commentaire.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#20)]  
  
### <a name="to-delete-a-comment-from-an-excel-range"></a>Pour supprimer un commentaire d’une plage Excel  
  
1.  Vérifiez qu’il existe un commentaire sur la plage et supprimez-le.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#19)]  
  
## <a name="see-also"></a>Voir aussi  
 [Travailler avec des feuilles de calcul](../vsto/working-with-worksheets.md)   
 [Comment : afficher des commentaires de feuille de calcul par programmation](../vsto/how-to-programmatically-display-worksheet-comments.md)   
 [NamedRange (contrôle)](../vsto/namedrange-control.md)  
  
  