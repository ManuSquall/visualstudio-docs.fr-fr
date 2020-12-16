---
title: 'Comment : redimensionner des contrôles dans des cellules de feuille de calcul'
description: Découvrez comment vous pouvez utiliser Visual Studio pour redimensionner des contrôles dans des cellules de feuille de calcul Microsoft Excel au moment de la conception et au moment de l’exécution.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: ba2a77dc44618c0415e645718aff3ead542b4b48
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525343"
---
# <a name="how-to-resize-controls-within-worksheet-cells"></a>Comment : redimensionner des contrôles dans des cellules de feuille de calcul
  Lorsque vous redimensionnez des colonnes ou des lignes dans une feuille de calcul, tous les contrôles hôtes dans les cellules se redimensionnent automatiquement à la hauteur ou à la largeur de la cellule qui a été redimensionnée. Par défaut, les contrôles Windows Forms ne sont pas redimensionnés automatiquement.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Si vous ajoutez les contrôles au moment du design, vous devez définir des options de positionnement pour chaque contrôle.

 Si vous ajoutez un contrôle de Windows Forms par programmation et fournissez un argument de plage, le contrôle se redimensionne automatiquement lorsqu’une cellule de la plage est redimensionnée. Pour plus d’informations, consultez [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="resize-controls-at-design-time"></a>Redimensionner les contrôles au moment du design

### <a name="to-make-controls-resize-with-cells-at-design-time"></a>Pour faire en sorte que les contrôles soient redimensionnés avec les cellules au moment du design

1. À partir de la **boîte à outils**, faites glisser un contrôle Windows Forms dans une feuille de calcul.

2. Cliquez avec le bouton droit sur le contrôle, puis cliquez sur **format de contrôle**.

3. Dans la boîte de dialogue **format de contrôle** , cliquez sur l’onglet **Propriétés** .

4. Sous **positionnement** de l’objet, sélectionnez l’option **déplacer et dimensionner avec les cellules** , puis cliquez sur **OK**.

     Lorsque vous redimensionnez la cellule qui contient le contrôle, le contrôle est redimensionné pour s’ajuster à la cellule.

## <a name="resize-controls-at-run-time"></a>Redimensionner les contrôles au moment de l’exécution
 Si vous ajoutez un contrôle Windows Forms au moment de l’exécution et que vous transmettez un <xref:Microsoft.Office.Interop.Excel.Range> comme emplacement du contrôle, le contrôle se redimensionne automatiquement lorsque la cellule de la feuille de calcul qui contient la plage est redimensionnée.

### <a name="to-make-controls-resize-with-cells-at-run-time"></a>Pour faire en sorte que les contrôles soient redimensionnés avec les cellules au moment de l’exécution

1. Ajoutez un contrôle à la plage a1.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#5)]

     Lorsque vous redimensionnez la cellule qui contient le contrôle, le contrôle est redimensionné pour s’ajuster à la cellule.

## <a name="reset-control-placement"></a>Réinitialiser le positionnement du contrôle
 Vous pouvez réinitialiser le positionnement et le redimensionnement du contrôle en affectant `Placement` à la propriété l’une des <xref:Microsoft.Office.Interop.Excel.XlPlacement> valeurs suivantes :

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>

### <a name="to-change-the-behavior-of-a-control-so-that-it-does-not-resize-or-move-with-the-cell"></a>Pour modifier le comportement d’un contrôle afin qu’il ne soit pas redimensionné ou déplacé avec la cellule

1. Appelez la propriété placement du contrôle et affectez la valeur à <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating> .

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#6)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#6)]

## <a name="see-also"></a>Voir aussi
- [Contrôles sur les documents Office](../vsto/controls-on-office-documents.md)
- [Comment : ajouter des contrôles Windows Forms à des documents Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Comment : masquer des contrôles sur des feuilles de calcul lors de l’impression](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Limitations des contrôles de Windows Forms sur les documents Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
