---
title: 'Procédure : Protéger des classeurs par programmation'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 12391f16e2797941cf83177aa1c83ed0dd2c0045
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56644599"
---
# <a name="how-to-programmatically-protect-workbooks"></a>Procédure : Protéger des classeurs par programmation
  Vous pouvez protéger un classeur Microsoft Office Excel afin que les utilisateurs ne peuvent pas ajouter ou supprimer des feuilles de calcul et également la protection du classeur par programmation. Vous pouvez éventuellement spécifier un mot de passe, indiquez si vous souhaitez que la structure protégée (de sorte que les utilisateurs ne peuvent pas déplacer les feuilles) et indiquez si vous souhaitez que les fenêtres du classeur protégés.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Protection d’un classeur n’empêche pas les utilisateurs de modifier les cellules. Pour protéger les données, vous devez protéger les feuilles de calcul. Pour plus d'informations, voir [Procédure : Protéger des feuilles de calcul par programmation](../vsto/how-to-programmatically-protect-worksheets.md).

 Les exemples de code suivants utilisent une variable pour contenir un mot de passe qui est obtenue à partir de l’utilisateur.

## <a name="protect-a-workbook-that-is-part-of-a-document-level-customization"></a>Protéger un classeur qui fait partie d’une personnalisation au niveau du document

### <a name="to-protect-a-workbook"></a>Pour protéger un classeur

1.  Appelez le <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> méthode du classeur et inclure un mot de passe. Pour utiliser l’exemple de code suivant, exécutez-le la `ThisWorkbook` classe, pas dans une classe de feuille.

     [!code-csharp[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#10)]
     [!code-vb[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#10)]

### <a name="to-unprotect-a-workbook"></a>Pour ôter la protection d’un classeur

1.  Appelez le <xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A> méthode, un mot de passe si nécessaire. Pour utiliser l’exemple de code suivant, exécutez-le la `ThisWorkbook` classe, pas dans une classe de feuille.

     [!code-csharp[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#11)]

## <a name="protect-a-workbook-by-using-an-application-level-add-in"></a>Protéger un classeur en utilisant un complément de niveau application dans

### <a name="to-protect-a-workbook"></a>Pour protéger un classeur

1.  Appelez le <xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A> méthode du classeur et inclure un mot de passe. Cet exemple de code utilise le classeur actif. Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisAddIn` dans votre projet.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#6)]

### <a name="to-unprotect-a-workbook"></a>Pour ôter la protection d’un classeur

1.  Appelez le <xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A> méthode du classeur actif, en passant un mot de passe si nécessaire. Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisAddIn` dans votre projet.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#7)]

## <a name="see-also"></a>Voir aussi
- [Travailler avec des classeurs](../vsto/working-with-workbooks.md)
- [Guide pratique pour Protéger des feuilles de calcul par programmation](../vsto/how-to-programmatically-protect-worksheets.md)
- [Guide pratique pour Masquer des feuilles de calcul par programmation](../vsto/how-to-programmatically-hide-worksheets.md)
- [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
