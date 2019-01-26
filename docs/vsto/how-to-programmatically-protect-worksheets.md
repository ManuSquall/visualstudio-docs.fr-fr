---
title: 'Procédure : Protéger des feuilles de calcul par programmation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- protection, adding to worksheets
- documents [Office development in Visual Studio], document protection
- document protection, adding to worksheets
- worksheets, protecting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1cd97cc6f85930523b6f0be02385dcb85b7af93d
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872779"
---
# <a name="how-to-programmatically-protect-worksheets"></a>Procédure : Protéger des feuilles de calcul par programmation
  La fonctionnalité de protection de Microsoft Office Excel permet d’empêcher les utilisateurs et le code de modifier des objets dans une feuille de calcul. Par défaut, toutes les cellules sont verrouillées une fois que vous avez activé la protection.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Dans les personnalisations au niveau du document, vous pouvez protéger les feuilles de calcul à l'aide du Concepteur Excel. Vous pouvez également protéger une feuille de calcul par programmation au moment de l'exécution dans n'importe quel type de projet.  
  
> [!NOTE]  
>  Vous ne pouvez pas ajouter de contrôles Windows Forms aux zones protégées d'une feuille de calcul.  
  
## <a name="use-the-designer"></a>Utiliser le Concepteur  
  
### <a name="to-protect-a-worksheet-in-the-designer"></a>Pour protéger une feuille de calcul dans le concepteur  
  
1. Dans le **modifications** groupe de la **révision** , cliquez sur **protéger la feuille**.  
  
    Le **protéger la feuille** boîte de dialogue s’affiche. Vous pouvez définir un mot de passe et spécifier éventuellement certaines actions que les utilisateurs sont autorisés à effectuer sur la feuille de calcul, par exemple appliquer un format aux cellules ou insérer des lignes.  
  
   Vous pouvez également autoriser les utilisateurs à modifier des plages spécifiques dans les feuilles de calcul protégées.  
  
### <a name="to-allow-editing-in-specific-ranges"></a>Pour autoriser les modifications dans des plages spécifiques  
  
1.  Dans le **modifications** groupe de la **révision** , cliquez sur **permettre aux utilisateurs de modifier des plages**.  
  
     Le **permettre aux utilisateurs de modifier des plages** boîte de dialogue s’affiche. Vous pouvez spécifier les plages qui sont déverrouillées à l'aide d'un mot de passe, et désigner les utilisateurs qui peuvent modifier les plages sans mot de passe.  
  
## <a name="use-code-at-runtime"></a>Utilisez le code lors de l’exécution  
 Le code suivant définit le mot de passe (à l'aide de la variable getPasswordFromUser, qui contient un mot de passe fourni par l'utilisateur) et autorise uniquement le tri.  
  
### <a name="to-protect-a-worksheet-by-using-code-in-a-document-level-customization"></a>Pour protéger une feuille de calcul en utilisant du code dans une personnalisation au niveau du document  
  
1.  Appelez la méthode <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> de la feuille de calcul. Cet exemple suppose que vous utilisez une feuille de calcul nommée `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#27](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomation#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#27)]  
  
### <a name="to-protect-a-worksheet-by-using-code-in-a-vsto-add-in"></a>Pour protéger une feuille de calcul en utilisant du code dans un complément VSTO  
  
1.  Appelez la méthode <xref:Microsoft.Office.Interop.Excel._Worksheet.Protect%2A> de la feuille de calcul active.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#17](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#17](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#17)]  
  
## <a name="see-also"></a>Voir aussi  
 [Travailler avec des feuilles de calcul](../vsto/working-with-worksheets.md)   
 [Guide pratique pour Supprimer par programmation la protection des feuilles de calcul](../vsto/how-to-programmatically-remove-protection-from-worksheets.md)   
 [Guide pratique pour Protéger des classeurs par programmation](../vsto/how-to-programmatically-protect-workbooks.md)   
 [Guide pratique pour Masquer des feuilles de calcul par programmation](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Éléments hôtes et la vue d’ensemble des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Élément hôte de feuille de calcul](../vsto/worksheet-host-item.md)   
 [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
