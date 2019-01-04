---
title: 'Procédure : Supprimer par programmation des feuilles de calcul des classeurs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, deleting worksheets
- worksheets, deleting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7254ba703c0e25d37dd3582d4443a6bdf1653a96
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53843383"
---
# <a name="how-to-programmatically-delete-worksheets-from-workbooks"></a>Procédure : Supprimer par programmation des feuilles de calcul des classeurs
  Vous pouvez supprimer toute feuille de calcul dans un classeur. Pour supprimer une feuille de calcul, utilisez l’élément hôte de feuille de calcul ou accédez à la feuille de calcul à l’aide de la collection Sheets du classeur.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="use-the-worksheet-host-item"></a>Utilisez l’élément hôte de feuille de calcul  
 Si la feuille de calcul a été ajoutée au moment du design dans une personnalisation au niveau du document, utilisez la méthode <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> pour supprimer une feuille de calcul spécifiée. Le code ci-dessous supprime une feuille de calcul d'un classeur en référençant directement l'élément hôte de feuille de calcul.  
  
> [!IMPORTANT]
>  Ce code s'exécute uniquement dans les projets que vous créez à l'aide des modèles de projet suivants :  
> 
> - Classeur Excel 2013  
> - Modèle Excel 2013  
> - Classeur Excel 2010  
> - Modèle Excel 2010  
> 
>   Si vous souhaitez effectuer cette tâche dans n’importe quel autre type de projet, vous devez ajouter une référence à la **Microsoft.Office.Interop.Excel** assembly et que vous devez utiliser des classes de cet assembly pour ouvrir un classeur et supprimer une feuille de calcul. Pour plus d'informations, voir [Procédure : Cibler les applications Office via les assemblys PIA](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) et [référence d’assembly PIA Excel 2010](http://go.microsoft.com/fwlink/?LinkId=189585).  
  
### <a name="to-delete-a-worksheet-by-using-a-worksheet-host-item"></a>Pour supprimer une feuille de calcul à l'aide d'un élément hôte de feuille de calcul  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> de `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#17](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomation#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#17)]  
  
## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Utilisez la collection Sheets du classeur Excel  
 Accédez aux feuilles de calcul via la collection <xref:Microsoft.Office.Interop.Excel.Sheets> Microsoft Office Excel dans les cas suivants :  
  
- Vous souhaitez supprimer une feuille de calcul dans un complément VSTO.  
  
- La feuille de calcul à supprimer a été créée au moment de l'exécution dans une personnalisation au niveau du document.  
  
  Le code suivant supprime une feuille de calcul d’un classeur en référençant la feuille avec le numéro d’index de la **feuilles** collection. Ce code suppose qu'une nouvelle feuille de calcul a été créée par programmation.  
  
> [!IMPORTANT]  
>  Si vous souhaitez effectuer cette tâche dans n’importe quel autre type de projet, vous devez ajouter une référence à la **Microsoft.Office.Interop.Excel** assembly et que vous devez utiliser des classes de cet assembly pour ouvrir un classeur et supprimer une feuille de calcul. Pour plus d'informations, voir [Procédure : Cibler les applications Office via les assemblys PIA](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) et [référence d’assembly PIA Excel 2010](http://go.microsoft.com/fwlink/?LinkId=189585).  
  
### <a name="to-delete-a-worksheet-by-using-the-sheets-collection-of-the-excel-workbook"></a>Pour supprimer une feuille de calcul à l’aide de la collection Sheets du classeur Excel  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Excel._Worksheet.Delete%2A> de la collection <xref:Microsoft.Office.Interop.Excel.Sheets>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#18](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomation#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#18)]  
  
## <a name="see-also"></a>Voir aussi  
 [Travailler avec des feuilles de calcul](../vsto/working-with-worksheets.md)   
 [Guide pratique pour Masquer des feuilles de calcul par programmation](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Guide pratique pour Déplacer des feuilles de calcul dans les classeurs par programmation](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [Guide pratique pour Sélectionnez par programmation des feuilles de calcul](../vsto/how-to-programmatically-select-worksheets.md)   
 [Guide pratique pour Ajouter par programmation des feuilles de calcul à des classeurs](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Élément hôte de feuille de calcul](../vsto/worksheet-host-item.md)   
 [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Limitations de programmation des éléments hôtes et contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
