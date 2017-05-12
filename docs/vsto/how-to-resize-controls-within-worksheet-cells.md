---
title: "Comment&#160;: redimensionner des contr&#244;les dans des cellules de feuille de calcul"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "contrôles (développement Office dans Visual Studio), redimensionner"
  - "contrôles managés, redimensionner"
  - "contrôles Windows Forms (développement Office dans Visual Studio), redimensionner"
  - "feuilles de calcul, redimensionner"
ms.assetid: 1439db4a-e64b-4381-a6e6-605ba94db3de
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Comment&#160;: redimensionner des contr&#244;les dans des cellules de feuille de calcul
  Lorsque vous redimensionnez des colonnes ou des lignes dans une feuille de calcul, tous les contrôles hôtes contenus dans les cellules sont automatiquement redimensionnés par rapport à la hauteur ou la largeur de la cellule qui a été redimensionnée.  Par défaut, les contrôles Windows Forms ne sont pas redimensionnés automatiquement.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Si vous ajoutez les contrôles au moment du design, vous devez définir des options de positionnement pour chaque contrôle.  
  
 Si vous ajoutez un contrôle Windows Forms par programmation et que vous fournissez un argument de plage, le contrôle est automatiquement redimensionné lorsqu'une cellule dans la plage est redimensionnée.  Pour plus d’informations, consultez [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## Redimensionnement des contrôles au moment du design  
  
#### Pour que les contrôles soient redimensionnés en même temps que les cellules au moment du design  
  
1.  À partir de la **boîte à outils**, faites glisser un contrôle Windows Forms vers une feuille de calcul.  
  
2.  Cliquez avec le bouton droit sur le contrôle et sélectionnez **Format de contrôle**.  
  
3.  Dans la boîte de dialogue **Format de contrôle**, cliquez sur l'onglet **Propriétés**.  
  
4.  Sous **Positionnement de l'objet**, sélectionnez l'option **Déplacer et dimensionner avec les cellules** et cliquez sur **OK**.  
  
     Lorsque vous redimensionnez la cellule qui contient le contrôle, le contrôle est redimensionné par rapport à la cellule.  
  
## Redimensionnement des contrôles au moment de l'exécution  
 Si vous ajoutez un contrôle Windows Forms au moment de l'exécution et passez une <xref:Microsoft.Office.Interop.Excel.Range> comme emplacement pour le contrôle, le contrôle sera automatiquement redimensionné en même temps que la cellule de la feuille de calcul qui le contient.  
  
#### Pour que les contrôles soient redimensionnés en même temps que les cellules au moment de l'exécution  
  
1.  Ajoutez un contrôle à la plage A1.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#5)]  
  
     Lorsque vous redimensionnez la cellule qui contient le contrôle, le contrôle est redimensionné par rapport à la cellule.  
  
## Réinitialisation du positionnement du contrôle  
 Pour réinitialiser le positionnement et le redimensionnement du contrôle, affectez à la propriété `Placement` l'une des valeurs <xref:Microsoft.Office.Interop.Excel.XlPlacement> suivantes :  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>  
  
#### Pour modifier le comportement d'un contrôle afin qu'il ne soit pas redimensionné ou déplacé avec la cellule  
  
1.  Appelez la propriété de positionnement du contrôle et affectez\-lui la valeur <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#6)]  
  
## Voir aussi  
 [Contrôles sur des documents Office](../vsto/controls-on-office-documents.md)   
 [Comment : ajouter des contrôles Windows Forms à des documents Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Comment : masquer des contrôles sur des feuilles de calcul lors de l'impression](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Limitations des contrôles Windows Forms dans les documents Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  