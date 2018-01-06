---
title: "Comment : redimensionner des contrôles dans les cellules de feuille de calcul | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- managed controls, resizing
- worksheets, resizing
- Windows Forms controls [Office development in Visual Studio], resizing
ms.assetid: 1439db4a-e64b-4381-a6e6-605ba94db3de
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 75759b501741329808198aafbc7dd39d0994cb98
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-resize-controls-within-worksheet-cells"></a>Comment : redimensionner des contrôles dans des cellules de feuille de calcul
  Lorsque vous redimensionnez des colonnes ou des lignes sur une feuille de calcul, tous les contrôles hôtes contenus dans les cellules automatiquement redimensionnent à la hauteur ou la largeur de la cellule qui a été redimensionnée. Contrôles Windows Forms ne se redimensionnent pas automatiquement par défaut.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Si vous ajoutez les contrôles au moment du design, vous devez définir d’options de positionnement pour chaque contrôle.  
  
 Si vous ajoutez un contrôle Windows Forms par programmation et fournissez un argument de plage, le contrôle se redimensionne automatiquement une cellule dans la plage est redimensionnée. Pour plus d'informations, consultez [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## <a name="resizing-controls-at-design-time"></a>Redimensionnement de contrôles au moment du Design  
  
#### <a name="to-make-controls-resize-with-cells-at-design-time"></a>Pour rendre des contrôles redimensionner des cellules au moment du design  
  
1.  À partir de la **boîte à outils**, faites glisser un contrôle Windows Forms à une feuille de calcul.  
  
2.  Cliquez sur le contrôle, puis cliquez sur **contrôle de Format**.  
  
3.  Dans le **contrôle de Format** boîte de dialogue, cliquez sur le **propriétés** onglet.  
  
4.  Sous **positionnement de l’objet**, sélectionnez le **déplacer et dimensionner avec les cellules** option, puis cliquez sur **OK**.  
  
     Lorsque vous redimensionnez la cellule qui contient le contrôle, le contrôle est redimensionné pour s’ajuster à la cellule.  
  
## <a name="resizing-controls-at-run-time"></a>Redimensionnement de contrôles au moment de l’exécution  
 Si vous ajoutez un contrôle Windows Forms au moment de l’exécution et que vous passez dans un <xref:Microsoft.Office.Interop.Excel.Range> comme emplacement pour le contrôle, le contrôle est redimensionné automatiquement lors du redimensionnement de la cellule de feuille de calcul qui contient la plage.  
  
#### <a name="to-make-controls-resize-with-cells-at-run-time"></a>Pour rendre des contrôles redimensionner des cellules en cours d’exécution  
  
1.  Ajouter un contrôle à la plage A1.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#5)]  
  
     Lorsque vous redimensionnez la cellule qui contient le contrôle, le contrôle est redimensionné pour s’ajuster à la cellule.  
  
## <a name="resetting-control-placement"></a>La réinitialisation d’un positionnement de contrôle  
 Vous pouvez réinitialiser le positionnement et le redimensionnement du contrôle en définissant le `Placement` propriété à une des opérations suivantes <xref:Microsoft.Office.Interop.Excel.XlPlacement> valeurs :  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>  
  
#### <a name="to-change-the-behavior-of-a-control-so-that-it-does-not-resize-or-move-with-the-cell"></a>Pour modifier le comportement d’un contrôle afin qu’il ne pas redimensionner ou déplacer avec la cellule  
  
1.  Appelez la propriété de positionnement du contrôle et définissez la valeur sur <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#6)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#6)]  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles sur des Documents Office](../vsto/controls-on-office-documents.md)   
 [Comment : ajouter des contrôles Windows Forms à des Documents Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Comment : masquer des contrôles sur des feuilles de calcul lors de l’impression](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Ajout de contrôles aux Documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Limitations des contrôles Windows Forms dans les documents Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  