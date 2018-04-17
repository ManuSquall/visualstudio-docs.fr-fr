---
title: 'Comment : protéger des classeurs par programmation | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 03cab4591bbca62c237877e39dabf40328768ccf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-protect-workbooks"></a>Comment : protéger des classeurs par programmation
  Vous pouvez protéger un classeur Microsoft Office Excel afin que les utilisateurs ne peuvent pas ajouter ou supprimer des feuilles de calcul et également ôter la protection du classeur par programmation. Vous pouvez éventuellement spécifier un mot de passe, indiquez si vous souhaitez que la structure soit protégée (de sorte que les utilisateurs ne peuvent pas déplacer les feuilles) et indiquez si vous souhaitez que les fenêtres du classeur protégés.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Protection d’un classeur n’arrête pas les utilisateurs de modifier les cellules. Pour protéger les données, vous devez protéger les feuilles de calcul. Pour plus d’informations, consultez [Comment : par programme protéger des feuilles de calcul](../vsto/how-to-programmatically-protect-worksheets.md).  
  
 Les exemples de code suivants utilisent une variable pour contenir un mot de passe est obtenu à partir de l’utilisateur.  
  
## <a name="protecting-a-workbook-that-is-part-of-a-document-level-customization"></a>Protection d’un classeur qui fait partie d’une personnalisation au niveau du Document  
  
#### <a name="to-protect-a-workbook"></a>Pour protéger un classeur  
  
1.  Appelez le <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> méthode du classeur et inclure un mot de passe. Pour utiliser l’exemple de code suivant, exécutez-le la `ThisWorkbook` classe et non dans une classe sheet.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#10)]
     [!code-vb[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#10)]  
  
#### <a name="to-unprotect-a-workbook"></a>Pour ôter la protection d’un classeur  
  
1.  Appelez le <xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A> méthode, un mot de passe si nécessaire. Pour utiliser l’exemple de code suivant, exécutez-le la `ThisWorkbook` classe et non dans une classe sheet.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#11)]  
  
## <a name="protecting-a-workbook-by-using-an-application-level-add-in"></a>Protection d’un classeur en utilisant un complément de niveau Application  
  
#### <a name="to-protect-a-workbook"></a>Pour protéger un classeur  
  
1.  Appelez le <xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A> méthode du classeur et inclure un mot de passe. Cet exemple de code utilise le classeur actif. Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisAddIn` dans votre projet.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#6)]  
  
#### <a name="to-unprotect-a-workbook"></a>Pour ôter la protection d’un classeur  
  
1.  Appelez le <xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A> méthode du classeur actif, en passant un mot de passe si nécessaire. Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisAddIn` dans votre projet.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des classeurs](../vsto/working-with-workbooks.md)   
 [Comment : protéger des feuilles de calcul par programmation](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Comment : masquer des feuilles de calcul par programmation](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  