---
title: 'Comment : protéger des classeurs par programmation'
description: Découvrez comment vous pouvez protéger un classeur Microsoft Excel afin que les utilisateurs ne puissent pas ajouter ou supprimer des feuilles de calcul, et également ôter la protection du classeur par programmation.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, passwords
- documents [Office development in Visual Studio], document protection
- workbooks, unprotecting
- document protection, removing from workbooks
- document protection, adding to workbooks
- workbooks, protecting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3b35b0fc234c3015275650ddb51e8ea3011c97a6
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528284"
---
# <a name="how-to-programmatically-protect-workbooks"></a>Comment : protéger des classeurs par programmation
  Vous pouvez protéger un classeur Excel Microsoft Office afin que les utilisateurs ne puissent pas ajouter ou supprimer des feuilles de calcul, et également ôter la protection du classeur par programmation. Vous pouvez éventuellement spécifier un mot de passe, indiquer si vous souhaitez que la structure soit protégée (afin que les utilisateurs ne puissent pas déplacer les feuilles) et indiquer si vous souhaitez que les fenêtres du classeur soient protégées.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 La protection d’un classeur n’empêche pas les utilisateurs de modifier les cellules. Pour protéger les données, vous devez protéger les feuilles de calcul. Pour plus d’informations, consultez [Comment : protéger des feuilles de calcul par programmation](../vsto/how-to-programmatically-protect-worksheets.md).

 Les exemples de code suivants utilisent une variable pour contenir un mot de passe obtenu de l’utilisateur.

## <a name="protect-a-workbook-that-is-part-of-a-document-level-customization"></a>Protéger un classeur qui fait partie d’une personnalisation au niveau du document

### <a name="to-protect-a-workbook"></a>Pour protéger un classeur

1. Appelez la <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> méthode du classeur et incluez un mot de passe. Pour utiliser l’exemple de code suivant, exécutez-le dans la `ThisWorkbook` classe, et non dans une classe de feuille.

     [!code-csharp[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#10)]
     [!code-vb[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#10)]

### <a name="to-unprotect-a-workbook"></a>Pour ôter la protection d’un classeur

1. Appelez la <xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A> méthode, en passant un mot de passe, le cas échéant. Pour utiliser l’exemple de code suivant, exécutez-le dans la `ThisWorkbook` classe, et non dans une classe de feuille.

     [!code-csharp[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#11)]

## <a name="protect-a-workbook-by-using-an-application-level-add-in"></a>Protéger un classeur à l’aide d’un complément au niveau de l’application

### <a name="to-protect-a-workbook"></a>Pour protéger un classeur

1. Appelez la <xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A> méthode du classeur et incluez un mot de passe. Cet exemple de code utilise le classeur actif. Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisAddIn` dans votre projet.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#6)]

### <a name="to-unprotect-a-workbook"></a>Pour ôter la protection d’un classeur

1. Appelez la <xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A> méthode du classeur actif, en passant un mot de passe, le cas échéant. Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisAddIn` dans votre projet.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#7)]

## <a name="see-also"></a>Voir aussi
- [Utiliser des classeurs](../vsto/working-with-workbooks.md)
- [Comment : protéger des feuilles de calcul par programmation](../vsto/how-to-programmatically-protect-worksheets.md)
- [Comment : masquer des feuilles de calcul par programmation](../vsto/how-to-programmatically-hide-worksheets.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
