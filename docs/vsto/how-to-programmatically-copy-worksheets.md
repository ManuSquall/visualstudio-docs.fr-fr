---
title: "Comment : copier des feuilles de calcul par programmation | Documents Microsoft"
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
- worksheets, copying
- Excel [Office development in Visual Studio], copying worksheets
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: fe8b289dd30ea44331a2ae0c63dd451da8969369
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-copy-worksheets"></a>Comment : copier des feuilles de calcul par programmation
  Vous pouvez créer une copie d'une feuille de calcul et insérer cette feuille de calcul avant ou après une feuille existante dans le classeur. Si vous ne spécifiez pas d'emplacement d'insertion de la feuille de calcul, Excel crée un nouveau classeur dans lequel la placer.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
> [!NOTE]  
>  Que vous copiiez la feuille de calcul par programmation ou que l'utilisateur final la copie manuellement, la nouvelle feuille de calcul n'a pas de code-behind et les contrôles sur la nouvelle feuille de calcul ne fonctionnent pas. Cela est dû au fait que la feuille de calcul récemment copiée est un objet <xref:Microsoft.Office.Interop.Excel.Worksheet>, non un élément hôte <xref:Microsoft.Office.Tools.Excel.Worksheet>. Les contrôles Windows Forms et les contrôles hôtes peuvent uniquement être ajoutés aux éléments hôtes. Pour plus d'informations, consultez [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
### <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-document-level-customization"></a>Pour ajouter une copie de feuille de calcul à un classeur dans une personnalisation au niveau du document  
  
1.  Utilisez la méthode <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> pour copier la première feuille de calcul du classeur actif et placez la copie après la troisième feuille.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#16)]  
  
### <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-vsto-add-in"></a>Pour ajouter une copie de feuille de calcul à un classeur dans un complément VSTO  
  
1.  Utilisez la méthode <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> pour copier la première feuille de calcul du classeur actif et placez la copie après la troisième feuille.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#12)]  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des feuilles de calcul](../vsto/working-with-worksheets.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Comment : ajouter par programmation des feuilles de calcul à des classeurs](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Comment : supprimer par programmation des feuilles de calcul des classeurs](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Comment : sélectionner par programme des feuilles de calcul](../vsto/how-to-programmatically-select-worksheets.md)   
 [Automatisation d’Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  