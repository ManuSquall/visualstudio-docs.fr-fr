---
title: 'Comment : masquer des contrôles sur des feuilles de calcul lors de l’impression | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- controls [Office development in Visual Studio], hiding while printing
- printing [Office development in Visual Studio], hiding controls
- worksheets, hiding controls when printing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4d02d823e707054fd17a5f3f892db41258b08081
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>Comment : masquer des contrôles sur des feuilles de calcul lors de l'impression
  Lorsque vous imprimez un document Microsoft Office Excel qui contient des contrôles Windows Forms, les contrôles sont visibles sur la feuille de calcul imprimée. Vous pouvez masquer les contrôles lors de l’impression d’une feuille de calcul.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Si vous masquez des contrôles qui affichent des données, comme un <xref:Microsoft.Office.Tools.Excel.Controls.TextBox>, les données dans le contrôle ne sera pas visibles sur la feuille de calcul imprimée.  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l’interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L’édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-hide-controls-when-a-worksheet-is-printed"></a>Pour masquer des contrôles lorsqu’une feuille de calcul est imprimée.  
  
1.  Créez ou ouvrez un projet Excel dans Visual Studio et vérifiez que **Feuil1** est visible dans le concepteur. Pour plus d’informations sur la création de projets, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  À partir de la **contrôles communs** onglet de la **boîte à outils**, faites glisser un <xref:Microsoft.Office.Tools.Excel.Controls.Button> le contrôle à une cellule sur `Sheet1`.  
  
3.  Dans le **propriétés** , configurez la <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> propriété **False**.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles sur des Documents Office](../vsto/controls-on-office-documents.md)   
 [Contrôles Windows Forms dans une vue d’ensemble des Documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Comment : ajouter des contrôles Windows Forms à des Documents Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Guide pratique pour redimensionner des contrôles dans des cellules de feuille de calcul](../vsto/how-to-resize-controls-within-worksheet-cells.md)  
  
  