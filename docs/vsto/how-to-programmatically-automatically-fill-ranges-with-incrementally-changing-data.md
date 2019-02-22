---
title: 'Procédure : Remplir par programmation automatiquement des plages avec des données soumises à modification incrémentielle'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 36a91875d2964bf952f039a699da6ed165afa090
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56638528"
---
# <a name="how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data"></a>Procédure : Remplir par programmation automatiquement des plages avec des données soumises à modification incrémentielle
  Le <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> méthode de la <xref:Microsoft.Office.Interop.Excel.Range> objet vous permet de remplir une plage dans une feuille de calcul avec des valeurs automatiquement. En règle générale, le <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> méthode est utilisée pour stocker de façon incrémentielle valeurs croissantes ou décroissantes dans une plage. Vous pouvez spécifier le comportement en fournissant une constante facultative à partir de la <xref:Microsoft.Office.Interop.Excel.XlAutoFillType> énumération.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Vous devez spécifier deux plages lors de l’utilisation <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>:

-   La plage qui appelle le <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> (méthode), qui spécifie le point de départ du remplissage et contient une valeur initiale.

-   La plage que vous souhaitez remplir, passée en tant que paramètre à la <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> (méthode). Cette plage de destination doit inclure la plage qui contient la valeur initiale.

    > [!NOTE]
    >  Vous ne pouvez pas passer un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôler à la place de la <xref:Microsoft.Office.Interop.Excel.Range>. Pour plus d’informations, consultez [limitations de programmation des éléments hôtes et contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

## <a name="example"></a>Exemple
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#49)]

## <a name="compile-the-code"></a>Compiler le code
 La première cellule de la plage que vous souhaitez remplir doit contenir une valeur initiale.

 L’exemple nécessite que vous remplissez les trois régions :

-   La colonne B consiste à inclure les cinq jours de la semaine. Pour la valeur initiale, tapez **lundi** dans la cellule B1.

-   La colonne C consiste à inclure les cinq mois. Pour la valeur initiale, tapez **janvier** dans la cellule C1.

-   La colonne D consiste à inclure une série de nombres, incrémentation par deux pour chaque ligne. Pour les valeurs initiales, tapez **4** dans la cellule D1 et **6** dans la cellule D2.

## <a name="see-also"></a>Voir aussi
- [Travailler avec des plages](../vsto/working-with-ranges.md)
- [Guide pratique pour Faire référence par programmation aux plages de feuille de calcul dans le code](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Guide pratique pour Appliquer des styles à des plages dans les classeurs par programmation](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Guide pratique pour Exécuter des calculs Excel par programmation](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [Éléments hôtes et la vue d’ensemble des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
- [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)
