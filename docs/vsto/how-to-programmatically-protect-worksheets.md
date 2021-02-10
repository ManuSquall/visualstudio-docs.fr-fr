---
title: 'Comment : protéger des feuilles de calcul par programmation'
description: Découvrez comment vous pouvez utiliser la fonctionnalité de protection de Microsoft Excel pour empêcher les utilisateurs et le code de modifier des objets dans une feuille de calcul.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 92ded3d8320f58bdd200f3892dc40c7a915c502e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963820"
---
# <a name="how-to-programmatically-protect-worksheets"></a>Comment : protéger des feuilles de calcul par programmation
  La fonctionnalité de protection de Microsoft Office Excel permet d’empêcher les utilisateurs et le code de modifier des objets dans une feuille de calcul. Par défaut, toutes les cellules sont verrouillées une fois que vous avez activé la protection.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Dans les personnalisations au niveau du document, vous pouvez protéger les feuilles de calcul à l'aide du Concepteur Excel. Vous pouvez également protéger une feuille de calcul par programmation au moment de l'exécution dans n'importe quel type de projet.

> [!NOTE]
> Vous ne pouvez pas ajouter de contrôles Windows Forms aux zones protégées d'une feuille de calcul.

## <a name="use-the-designer"></a>Utiliser le concepteur

### <a name="to-protect-a-worksheet-in-the-designer"></a>Pour protéger une feuille de calcul dans le concepteur

1. Dans le groupe **modifications** de l’onglet **révision** , cliquez sur **protéger la feuille**.

    La boîte de dialogue **protéger la feuille** s’affiche. Vous pouvez définir un mot de passe et spécifier éventuellement certaines actions que les utilisateurs sont autorisés à effectuer sur la feuille de calcul, par exemple appliquer un format aux cellules ou insérer des lignes.

   Vous pouvez également autoriser les utilisateurs à modifier des plages spécifiques dans les feuilles de calcul protégées.

### <a name="to-allow-editing-in-specific-ranges"></a>Pour autoriser les modifications dans des plages spécifiques

1. Dans le groupe **modifications** de l’onglet **révision** , cliquez sur **autoriser les utilisateurs à modifier des plages**.

     La boîte **de dialogue autoriser les utilisateurs à modifier des plages** s’affiche. Vous pouvez spécifier les plages qui sont déverrouillées à l'aide d'un mot de passe, et désigner les utilisateurs qui peuvent modifier les plages sans mot de passe.

## <a name="use-code-at-run-time"></a>Utiliser du code au moment de l’exécution
 Le code suivant définit le mot de passe (à l'aide de la variable getPasswordFromUser, qui contient un mot de passe fourni par l'utilisateur) et autorise uniquement le tri.

### <a name="to-protect-a-worksheet-by-using-code-in-a-document-level-customization"></a>Pour protéger une feuille de calcul en utilisant du code dans une personnalisation au niveau du document

1. Appelez la méthode <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> de la feuille de calcul. Cet exemple suppose que vous utilisez une feuille de calcul nommée `Sheet1`.

     [!code-csharp[Trin_VstcoreExcelAutomation#27](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomation#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#27)]

### <a name="to-protect-a-worksheet-by-using-code-in-a-vsto-add-in"></a>Pour protéger une feuille de calcul en utilisant du code dans un complément VSTO

1. Appelez la méthode <xref:Microsoft.Office.Interop.Excel._Worksheet.Protect%2A> de la feuille de calcul active.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#17](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#17](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#17)]

## <a name="see-also"></a>Voir aussi
- [Utiliser des feuilles de calcul](../vsto/working-with-worksheets.md)
- [Comment : supprimer la protection des feuilles de calcul par programmation](../vsto/how-to-programmatically-remove-protection-from-worksheets.md)
- [Comment : protéger des classeurs par programmation](../vsto/how-to-programmatically-protect-workbooks.md)
- [Comment : masquer des feuilles de calcul par programmation](../vsto/how-to-programmatically-hide-worksheets.md)
- [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
- [Élément hôte de feuille de calcul](../vsto/worksheet-host-item.md)
- [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
