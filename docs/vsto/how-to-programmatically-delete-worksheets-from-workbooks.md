---
title: 'Comment : supprimer des feuilles de calcul à partir de classeurs par programmation'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, deleting worksheets
- worksheets, deleting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 38aa92ae1c320ae9eb5ad4bdb1e43b761048661f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547132"
---
# <a name="how-to-programmatically-delete-worksheets-from-workbooks"></a>Comment : supprimer des feuilles de calcul à partir de classeurs par programmation
  Vous pouvez supprimer toute feuille de calcul dans un classeur. Pour supprimer une feuille de calcul, utilisez l’élément hôte de feuille de calcul ou accédez à la feuille de calcul à l’aide de la collection Sheets du classeur.

 [!INCLUDE[appliesto_xlalldocapp](includes/appliesto-xlalldocapp-md.md)]

## <a name="use-the-worksheet-host-item"></a>Utiliser l’élément hôte de feuille de calcul
 Si la feuille de calcul a été ajoutée au moment du design dans une personnalisation au niveau du document, utilisez la méthode <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> pour supprimer une feuille de calcul spécifiée. Le code ci-dessous supprime une feuille de calcul d'un classeur en référençant directement l'élément hôte de feuille de calcul.

> [!IMPORTANT]
> Ce code s'exécute uniquement dans les projets que vous créez à l'aide des modèles de projet suivants :
>
> - Classeur Excel 2013
> - Modèle Excel 2013
> - Classeur Excel 2010
> - Modèle Excel 2010
>
>   Si vous souhaitez effectuer cette tâche dans tout autre type de projet, vous devez ajouter une référence à l’assembly **Microsoft. Office. Interop. Excel** , puis vous devez utiliser les classes de cet assembly pour ouvrir un classeur et supprimer une feuille de calcul. Pour plus d’informations, consultez [Guide pratique pour cibler des applications Office à l’aide d’assemblys PIA (Primary Interop](how-to-target-office-applications-through-primary-interop-assemblies.md) [assembly) et référence d’assembly PIA Excel 2010](office-primary-interop-assemblies.md).

### <a name="to-delete-a-worksheet-by-using-a-worksheet-host-item"></a>Pour supprimer une feuille de calcul à l'aide d'un élément hôte de feuille de calcul

1. Appelez la méthode <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> de `Sheet1`.

     [!code-csharp[Trin_VstcoreExcelAutomation#17](codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomation#17](codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#17)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Utiliser la collection Sheets du classeur Excel
 Accédez aux feuilles de calcul via la collection <xref:Microsoft.Office.Interop.Excel.Sheets> Microsoft Office Excel dans les cas suivants :

- Vous souhaitez supprimer une feuille de calcul dans un complément VSTO.

- La feuille de calcul à supprimer a été créée au moment de l'exécution dans une personnalisation au niveau du document.

  Le code suivant supprime une feuille de calcul d’un classeur en référençant la feuille à travers le numéro d’index de la collection de **feuilles** . Ce code suppose qu'une nouvelle feuille de calcul a été créée par programmation.

> [!IMPORTANT]
> Si vous souhaitez effectuer cette tâche dans tout autre type de projet, vous devez ajouter une référence à l’assembly **Microsoft. Office. Interop. Excel** , puis vous devez utiliser les classes de cet assembly pour ouvrir un classeur et supprimer une feuille de calcul. Pour plus d’informations, consultez [Guide pratique pour cibler des applications Office à l’aide d’assemblys PIA (Primary Interop](how-to-target-office-applications-through-primary-interop-assemblies.md) [assembly) et référence d’assembly PIA Excel 2010](office-primary-interop-assemblies.md).

### <a name="to-delete-a-worksheet-by-using-the-sheets-collection-of-the-excel-workbook"></a>Pour supprimer une feuille de calcul à l'aide de la collection Sheets du classeur Excel

1. Appelez la méthode <xref:Microsoft.Office.Interop.Excel._Worksheet.Delete%2A> de la collection <xref:Microsoft.Office.Interop.Excel.Sheets>.

     [!code-csharp[Trin_VstcoreExcelAutomation#18](codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomation#18](codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#18)]

## <a name="see-also"></a>Voir aussi
- [Utiliser des feuilles de calcul](working-with-worksheets.md)
- [Comment : masquer des feuilles de calcul par programmation](how-to-programmatically-hide-worksheets.md)
- [Comment : déplacer des feuilles de calcul dans des classeurs par programmation](how-to-programmatically-move-worksheets-within-workbooks.md)
- [Comment : sélectionner des feuilles de calcul par programmation](how-to-programmatically-select-worksheets.md)
- [Comment : ajouter des feuilles de calcul à des classeurs par programmation](how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Élément hôte de feuille de calcul](worksheet-host-item.md)
- [Accès global aux objets dans les projets Office](global-access-to-objects-in-office-projects.md)
- [Limitations de programmation des éléments hôtes et des contrôles hôtes](programmatic-limitations-of-host-items-and-host-controls.md)
