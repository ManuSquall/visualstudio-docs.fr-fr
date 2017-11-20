---
title: "Comment : masquer des contrôles sur des feuilles de calcul lors de l’impression | Documents Microsoft"
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
- printing [Office development in Visual Studio], worksheets
- controls [Office development in Visual Studio], hiding while printing
- printing [Office development in Visual Studio], hiding controls
- worksheets, hiding controls when printing
ms.assetid: a637fe9a-9de1-4162-8ff6-fe28ccd62389
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e89c2f986ffc71892682b9fc8ab60b8810850c2a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>Comment : masquer des contrôles sur des feuilles de calcul lors de l'impression
  Lorsque vous imprimez un document Microsoft Office Excel qui contient des contrôles Windows Forms, les contrôles sont visibles sur la feuille de calcul imprimée. Vous pouvez masquer les contrôles lors de l’impression d’une feuille de calcul.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Si vous masquez des contrôles qui affichent des données, comme un <xref:Microsoft.Office.Tools.Excel.Controls.TextBox>, les données dans le contrôle ne sera pas visibles sur la feuille de calcul imprimée.  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-hide-controls-when-a-worksheet-is-printed"></a>Pour masquer des contrôles lorsqu’une feuille de calcul est imprimée.  
  
1.  Créez ou ouvrez un projet Excel dans Visual Studio et vérifiez que **Feuil1** est visible dans le concepteur. Pour plus d’informations sur la création de projets, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  À partir de la **contrôles communs** onglet de la **boîte à outils**, faites glisser un <xref:Microsoft.Office.Tools.Excel.Controls.Button> le contrôle à une cellule sur `Sheet1`.  
  
3.  Dans le **propriétés** , configurez la <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> propriété **False**.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles sur des Documents Office](../vsto/controls-on-office-documents.md)   
 [Contrôles Windows Forms dans une vue d’ensemble des Documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Comment : ajouter des contrôles Windows Forms à des Documents Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Guide pratique pour redimensionner des contrôles dans des cellules de feuille de calcul](../vsto/how-to-resize-controls-within-worksheet-cells.md)  
  
  