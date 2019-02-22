---
title: 'Procédure : Redimensionner des contrôles dans les cellules de feuille de calcul'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- managed controls, resizing
- worksheets, resizing
- Windows Forms controls [Office development in Visual Studio], resizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d039de309e1e9d5ec80d469d4d1329aad7118e71
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56625463"
---
# <a name="how-to-resize-controls-within-worksheet-cells"></a>Procédure : Redimensionner des contrôles dans les cellules de feuille de calcul
  Lorsque vous redimensionnez des colonnes ou des lignes sur une feuille de calcul, tous les contrôles hôtes dans les cellules se redimensionnent automatiquement la hauteur ou largeur de la cellule qui a été redimensionnée. Contrôles Windows Forms ne se redimensionnent pas automatiquement par défaut.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Si vous ajoutez les contrôles au moment du design, vous devez définir des options pour chaque contrôle de positionnement.

 Si vous ajoutez un contrôle Windows Forms par programmation et que vous fournissez un argument de plage, le contrôle est redimensionné automatiquement lorsqu’une cellule dans la plage est redimensionnée. Pour plus d’informations, consultez [ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="resize-controls-at-design-time"></a>Redimensionner des contrôles au moment du design

### <a name="to-make-controls-resize-with-cells-at-design-time"></a>Pour que les contrôles à redimensionner des cellules au moment du design

1.  À partir de la **boîte à outils**, faites glisser un contrôle Windows Forms à une feuille de calcul.

2.  Cliquez sur le contrôle, puis cliquez sur **Format contrôle**.

3.  Dans le **Format contrôle** boîte de dialogue, cliquez sur le **propriétés** onglet.

4.  Sous **positionnement de l’objet**, sélectionnez le **déplacez et redimensionnez des cellules** option, puis cliquez sur **OK**.

     Lorsque vous redimensionnez la cellule qui contient le contrôle, le contrôle est redimensionné pour s’ajuster à la cellule.

## <a name="resize-controls-at-runtime"></a>Redimensionner des contrôles lors de l’exécution
 Si vous ajoutez un contrôle Windows Forms lors de l’exécution et que vous passez un <xref:Microsoft.Office.Interop.Excel.Range> comme emplacement pour le contrôle, le contrôle sera redimensionné automatiquement lorsque la cellule de feuille de calcul qui contient la plage est redimensionnée.

### <a name="to-make-controls-resize-with-cells-at-run-time"></a>Pour que les contrôles à redimensionner des cellules en cours d’exécution

1.  Ajouter un contrôle à la plage A1.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#5)]

     Lorsque vous redimensionnez la cellule qui contient le contrôle, le contrôle est redimensionné pour s’ajuster à la cellule.

## <a name="reset-control-placement"></a>Réinitialiser le positionnement de contrôle
 Vous pouvez réinitialiser le positionnement et redimensionnement du contrôle en définissant le `Placement` propriété à une des opérations suivantes <xref:Microsoft.Office.Interop.Excel.XlPlacement> valeurs :

-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>

-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>

-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>

### <a name="to-change-the-behavior-of-a-control-so-that-it-does-not-resize-or-move-with-the-cell"></a>Pour modifier le comportement d’un contrôle afin qu’il ne pas redimensionner ou déplacer la cellule

1.  Appelez la propriété de positionnement du contrôle et définissez la valeur sur <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#6)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#6)]

## <a name="see-also"></a>Voir aussi
- [Contrôles sur des documents Office](../vsto/controls-on-office-documents.md)
- [Guide pratique pour Ajouter des contrôles Windows Forms aux documents Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Guide pratique pour Masquer des contrôles sur des feuilles de calcul lors de l’impression](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Limitations des contrôles Windows Forms sur des documents Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
