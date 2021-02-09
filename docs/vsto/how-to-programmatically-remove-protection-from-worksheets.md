---
title: 'Comment : supprimer la protection des feuilles de calcul par programmation'
description: Découvrez comment vous pouvez utiliser Visual Studio pour supprimer par programmation la protection d’une feuille de calcul Microsoft Excel.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, unprotecting
- documents [Office development in Visual Studio], document protection
- document protection, removing from worksheets
- Unprotect method
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 85f659248528d0d7cf4357ffe2d1c2c5f88df9e9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906752"
---
# <a name="how-to-programmatically-remove-protection-from-worksheets"></a>Comment : supprimer la protection des feuilles de calcul par programmation
  Vous pouvez supprimer par programmation la protection d’une feuille de calcul Microsoft Office Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 L’exemple suivant utilise la variable `getPasswordFromUser`, qui contient un mot de passe fourni par l’utilisateur.

## <a name="to-unprotect-a-worksheet-in-a-document-level-customization"></a>Pour ôter la protection d’une feuille de calcul dans une personnalisation au niveau du document

1. Appelez la <xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A> méthode de la feuille de calcul et transmettez le mot de passe, si nécessaire. Cet exemple suppose que vous utilisez une feuille de calcul nommée `Sheet1`.

     [!code-csharp[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#28)]

## <a name="to-unprotect-a-worksheet-in-a-vsto-add-in"></a>Pour ôter la protection d’une feuille de calcul dans un complément VSTO

1. Appelez la <xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A> méthode de la feuille de calcul active et transmettez le mot de passe, si nécessaire.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#18)]

## <a name="see-also"></a>Voir aussi
- [Utiliser des feuilles de calcul](../vsto/working-with-worksheets.md)
- [Comment : protéger des feuilles de calcul par programmation](../vsto/how-to-programmatically-protect-worksheets.md)
- [Comment : protéger des classeurs par programmation](../vsto/how-to-programmatically-protect-workbooks.md)
- [Comment : masquer des feuilles de calcul par programmation](../vsto/how-to-programmatically-hide-worksheets.md)
- [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)
