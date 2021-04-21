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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9f0b479c56be6da7b14f87263c8c01d66910ac20
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827107"
---
# <a name="how-to-programmatically-protect-workbooks"></a>Comment : protéger des classeurs par programmation
  Vous pouvez protéger un classeur Excel Microsoft Office afin que les utilisateurs ne puissent pas ajouter ou supprimer des feuilles de calcul, et également ôter la protection du classeur par programmation. Vous pouvez éventuellement spécifier un mot de passe, indiquer si vous souhaitez que la structure soit protégée (afin que les utilisateurs ne puissent pas déplacer les feuilles) et indiquer si vous souhaitez que les fenêtres du classeur soient protégées.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 La protection d’un classeur n’empêche pas les utilisateurs de modifier les cellules. Pour protéger les données, vous devez protéger les feuilles de calcul. Pour plus d’informations, consultez [Comment : protéger des feuilles de calcul par programmation](../vsto/how-to-programmatically-protect-worksheets.md).

 Les exemples de code suivants utilisent une variable pour contenir un mot de passe obtenu de l’utilisateur.

## <a name="protect-a-workbook-that-is-part-of-a-document-level-customization"></a>Protéger un classeur qui fait partie d’une personnalisation au niveau du document

### <a name="to-protect-a-workbook"></a>Pour protéger un classeur

1. Appelez la <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> méthode du classeur et incluez un mot de passe. Pour utiliser l’exemple de code suivant, exécutez-le dans la `ThisWorkbook` classe, et non dans une classe de feuille.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet10":::

### <a name="to-unprotect-a-workbook"></a>Pour ôter la protection d’un classeur

1. Appelez la <xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A> méthode, en passant un mot de passe, le cas échéant. Pour utiliser l’exemple de code suivant, exécutez-le dans la `ThisWorkbook` classe, et non dans une classe de feuille.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet11":::

## <a name="protect-a-workbook-by-using-an-application-level-add-in"></a>Protéger un classeur à l’aide d’un complément au niveau de l’application

### <a name="to-protect-a-workbook"></a>Pour protéger un classeur

1. Appelez la <xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A> méthode du classeur et incluez un mot de passe. Cet exemple de code utilise le classeur actif. Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisAddIn` dans votre projet.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet6":::

### <a name="to-unprotect-a-workbook"></a>Pour ôter la protection d’un classeur

1. Appelez la <xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A> méthode du classeur actif, en passant un mot de passe, le cas échéant. Pour utiliser cet exemple, exécutez le code à partir de la classe `ThisAddIn` dans votre projet.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet7":::

## <a name="see-also"></a>Voir aussi
- [Utiliser des classeurs](../vsto/working-with-workbooks.md)
- [Comment : protéger des feuilles de calcul par programmation](../vsto/how-to-programmatically-protect-worksheets.md)
- [Comment : masquer des feuilles de calcul par programmation](../vsto/how-to-programmatically-hide-worksheets.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
