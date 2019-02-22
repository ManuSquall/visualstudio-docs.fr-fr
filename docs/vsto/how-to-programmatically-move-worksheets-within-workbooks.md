---
title: 'Procédure : Déplacer des feuilles de calcul dans les classeurs par programmation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, moving
- workbooks, moving worksheets in
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 20ca03e8d7a3c574501d879cf9949d26fd7ba3a3
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56595735"
---
# <a name="how-to-programmatically-move-worksheets-within-workbooks"></a>Procédure : Déplacer des feuilles de calcul dans les classeurs par programmation
  Vous pouvez modifier par programmation la position des feuilles de calcul les unes par rapport aux autres dans un classeur. Si vous ne spécifiez pas d’emplacement pour la feuille déplacée, Excel crée un classeur pour le contenir.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-move-a-worksheet-in-a-document-level-customization"></a>Pour déplacer une feuille de calcul dans une personnalisation au niveau du document

1.  Affectez le nombre total de feuilles dans le classeur à une variable, puis déplacez la première feuille de calcul pour qu’elle devienne la dernière.

     [!code-csharp[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#24)]

## <a name="to-move-a-worksheet-in-a-vsto-add-in"></a>Pour déplacer une feuille de calcul dans un composant logiciel complément VSTO

1.  Affectez le nombre total de feuilles dans le classeur à une variable, puis déplacez la première feuille de calcul pour qu’elle devienne la dernière.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#16)]

## <a name="see-also"></a>Voir aussi
- [Travailler avec des feuilles de calcul](../vsto/working-with-worksheets.md)
- [Guide pratique pour Masquer des feuilles de calcul par programmation](../vsto/how-to-programmatically-hide-worksheets.md)
- [Guide pratique pour Supprimer par programmation des feuilles de calcul des classeurs](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Guide pratique pour Protéger des feuilles de calcul par programmation](../vsto/how-to-programmatically-protect-worksheets.md)
- [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)
