---
title: "Comment : déplacer des feuilles de calcul dans les classeurs par programmation | Documents Microsoft"
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
- worksheets, moving
- workbooks, moving worksheets in
ms.assetid: a010a633-412e-4299-9587-cacb035842c1
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 12597413fccfc9b7b43b322085e36148981be9db
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-move-worksheets-within-workbooks"></a>Comment : déplacer des feuilles de calcul dans les classeurs par programmation
  Vous pouvez modifier par programmation la position des feuilles de calcul les unes par rapport aux autres dans un classeur. Si vous ne spécifiez pas d’emplacement pour la feuille déplacée, Excel crée un classeur pour le contenir.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-move-a-worksheet-in-a-document-level-customization"></a>Pour déplacer une feuille de calcul dans une personnalisation au niveau du document  
  
1.  Affectez le nombre total de feuilles dans le classeur à une variable, puis déplacez la première feuille de calcul pour qu’elle devienne la dernière.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#24)]  
  
### <a name="to-move-a-worksheet-in-an-vsto-add-in"></a>Pour déplacer une feuille de calcul dans un complément VSTO  
  
1.  Affectez le nombre total de feuilles dans le classeur à une variable, puis déplacez la première feuille de calcul pour qu’elle devienne la dernière.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#16)]  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des feuilles de calcul](../vsto/working-with-worksheets.md)   
 [Comment : masquer des feuilles de calcul par programmation](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Comment : supprimer par programmation des feuilles de calcul des classeurs](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Comment : protéger des feuilles de calcul par programmation](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)  
  
  