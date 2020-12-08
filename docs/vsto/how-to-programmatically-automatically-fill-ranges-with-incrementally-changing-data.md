---
title: Remplissage automatique des plages de données à modification incrémentielle par programmation
description: Découvrez comment la méthode de remplissage automatique de l’objet Range vous permet de remplir automatiquement une plage dans une feuille de calcul avec des valeurs.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Autofill method [Excel]
- filling ranges automatically
- ranges, automatically filling
- workbooks, filling ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dc80b4b589eb46aefa9ef6d75384ed17bb1b7c8c
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847206"
---
# <a name="how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data"></a>Comment : remplir automatiquement des plages par programmation avec des données à modification incrémentielle
  La <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> méthode de l' <xref:Microsoft.Office.Interop.Excel.Range> objet vous permet de remplir automatiquement une plage dans une feuille de calcul avec des valeurs. La plupart du temps, la <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> méthode est utilisée pour stocker de façon incrémentielle des valeurs croissantes ou décroissantes dans une plage. Vous pouvez spécifier le comportement en fournissant une constante facultative à partir de l' <xref:Microsoft.Office.Interop.Excel.XlAutoFillType> énumération.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Vous devez spécifier deux plages lors de l’utilisation de <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> :

- Plage qui appelle la <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> méthode, qui spécifie le point de départ du remplissage et contient une valeur initiale.

- Plage que vous souhaitez remplir, transmise en tant que paramètre à la <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> méthode. Cette plage de destination doit inclure la plage qui contient la valeur initiale.

    > [!NOTE]
    > Vous ne pouvez pas passer un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle à la place de <xref:Microsoft.Office.Interop.Excel.Range> . Pour plus d’informations, consultez [limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

## <a name="example"></a> Exemple
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#49)]

## <a name="compile-the-code"></a>Compiler le code
 La première cellule de la plage que vous souhaitez remplir doit contenir une valeur initiale.

 L’exemple requiert la saisie de trois régions :

- La colonne B doit inclure cinq jours de semaine. Pour la valeur initiale, tapez **Monday** dans la cellule B1.

- La colonne C doit inclure cinq mois. Pour la valeur initiale, tapez **January** dans la cellule C1.

- La colonne D consiste à inclure une série de nombres, en incrémentant de deux pour chaque ligne. Pour les valeurs initiales, tapez **4** dans la cellule D1 et **6** dans la cellule D2.

## <a name="see-also"></a>Voir aussi
- [Utiliser des plages](../vsto/working-with-ranges.md)
- [Comment : faire référence aux plages de la feuille de calcul dans le code par programmation](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Comment : appliquer des styles à des plages dans des classeurs par programmation](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Comment : exécuter des calculs Excel par programmation](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
- [Paramètres facultatifs dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
