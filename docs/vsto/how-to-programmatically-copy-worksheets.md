---
title: 'Comment : copier des feuilles de calcul par programmation'
description: Découvrez comment vous pouvez créer une copie d’une feuille de calcul et insérer cette feuille de calcul avant ou après une feuille de calcul existante dans le classeur.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying
- Excel [Office development in Visual Studio], copying worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2a5b24d7896ec1f81c7e8d5d4c41a5e6af807b13
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828577"
---
# <a name="how-to-programmatically-copy-worksheets"></a>Comment : copier des feuilles de calcul par programmation
  Vous pouvez créer une copie d'une feuille de calcul et insérer cette feuille de calcul avant ou après une feuille existante dans le classeur. Si vous ne spécifiez pas d'emplacement d'insertion de la feuille de calcul, Excel crée un nouveau classeur dans lequel la placer.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

> [!NOTE]
> Que vous copiiez la feuille de calcul par programmation ou que l'utilisateur final la copie manuellement, la nouvelle feuille de calcul n'a pas de code-behind et les contrôles sur la nouvelle feuille de calcul ne fonctionnent pas. Cela est dû au fait que la feuille de calcul récemment copiée est un objet <xref:Microsoft.Office.Interop.Excel.Worksheet>, non un élément hôte <xref:Microsoft.Office.Tools.Excel.Worksheet>. Les contrôles Windows Forms et les contrôles hôtes peuvent uniquement être ajoutés aux éléments hôtes. Pour plus d’informations, consultez [limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-document-level-customization"></a>Pour ajouter une copie de feuille de calcul à un classeur dans une personnalisation au niveau du document

1. Utilisez la méthode <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> pour copier la première feuille de calcul du classeur actif et placez la copie après la troisième feuille.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet16":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet16":::

## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-vsto-add-in"></a>Pour ajouter une copie de feuille de calcul à un classeur dans un complément VSTO

1. Utilisez la méthode <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> pour copier la première feuille de calcul du classeur actif et placez la copie après la troisième feuille.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet12":::

## <a name="see-also"></a>Voir aussi
- [Utiliser des feuilles de calcul](../vsto/working-with-worksheets.md)
- [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
- [Comment : ajouter des feuilles de calcul à des classeurs par programmation](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Comment : supprimer des feuilles de calcul à partir de classeurs par programmation](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Comment : sélectionner des feuilles de calcul par programmation](../vsto/how-to-programmatically-select-worksheets.md)
- [Automatiser Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)
- [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
