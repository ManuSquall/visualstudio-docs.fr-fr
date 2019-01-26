---
title: 'Procédure : Supprimer par programmation la protection des feuilles de calcul'
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b94375b54e7e0c0c774adc7b8054fc4219456a40
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870085"
---
# <a name="how-to-programmatically-remove-protection-from-worksheets"></a>Procédure : Supprimer par programmation la protection des feuilles de calcul
  Vous pouvez supprimer par programmation la protection d’une feuille de calcul Microsoft Office Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 L’exemple suivant utilise la variable `getPasswordFromUser`, qui contient un mot de passe fourni par l’utilisateur.  
  
## <a name="to-unprotect-a-worksheet-in-a-document-level-customization"></a>Pour ôter la protection d’une feuille de calcul dans une personnalisation au niveau du document  
  
1.  Appelez le <xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A> méthode de la feuille de calcul et passez le mot de passe, si nécessaire. Cet exemple suppose que vous utilisez une feuille de calcul nommée `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#28)]  
  
## <a name="to-unprotect-a-worksheet-in-a-vsto-add-in"></a>Pour ôter la protection d’une feuille de calcul dans un composant logiciel complément VSTO  
  
1.  Appelez le <xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A> méthode de la feuille de calcul active et passez le mot de passe, si nécessaire.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#18)]  
  
## <a name="see-also"></a>Voir aussi  
 [Travailler avec des feuilles de calcul](../vsto/working-with-worksheets.md)   
 [Guide pratique pour Protéger des feuilles de calcul par programmation](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Guide pratique pour Protéger des classeurs par programmation](../vsto/how-to-programmatically-protect-workbooks.md)   
 [Guide pratique pour Masquer des feuilles de calcul par programmation](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)  
