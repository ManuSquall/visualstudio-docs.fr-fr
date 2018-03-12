---
title: "Comment : liste par programmation les derniers fichiers de classeur utilisés | Documents Microsoft"
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
- workbooks, listing recently used
- RecentFiles property
- Excel [Office development in Visual Studio], recently used files listing
- recent file list, Excel
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: e8a64f8a934e8cd7cdbbed11a87d15e795d19d0f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>Comment : répertorier les fichiers de classeur récemment utilisés par programmation
  Le <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> propriété retourne une collection qui contient les noms de tous les fichiers qui apparaissent dans la liste de Microsoft Office Excel des fichiers récemment utilisés. La longueur de la liste varie en fonction du nombre de fichiers que l’utilisateur a choisi de conserver. Vous pouvez afficher les résultats dans une plage.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Pour afficher la liste récemment des classeurs utilisés dans un objet range  
  
1.  Parcourez la liste des fichiers récents et afficher les noms dans les cellules relatif à un <xref:Microsoft.Office.Interop.Excel.Range> objet.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des classeurs](../vsto/working-with-workbooks.md)   
 [NamedRange (contrôle)](../vsto/namedrange-control.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  