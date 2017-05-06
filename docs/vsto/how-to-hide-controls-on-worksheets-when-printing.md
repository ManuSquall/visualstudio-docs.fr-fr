---
title: "Comment&#160;: masquer des contr&#244;les sur des feuilles de calcul lors de l&#39;impression"
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
  - "contrôles (développement Office dans Visual Studio), masquer lors de l'impression"
  - "imprimer (développement Office dans Visual Studio), masquer les contrôles"
  - "imprimer (développement Office dans Visual Studio), feuilles de calcul"
  - "feuilles de calcul, masquer les contrôles pendant l'impression"
ms.assetid: a637fe9a-9de1-4162-8ff6-fe28ccd62389
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Comment&#160;: masquer des contr&#244;les sur des feuilles de calcul lors de l&#39;impression
  Lorsque vous imprimez un document Microsoft Office Excel qui contient des contrôles Windows Forms, les contrôles sont visibles sur la feuille de calcul imprimée.  Vous pouvez masquer les contrôles lors de l'impression d'une feuille de calcul.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Si vous masquez des contrôles qui affichent des données, tels qu'un contrôle <xref:Microsoft.Office.Tools.Excel.Controls.TextBox>, les données du contrôle ne seront pas visibles sur la feuille de calcul imprimée.  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes.  Ces éléments dépendent de l'édition de Visual Studio dont vous disposez et des paramètres que vous utilisez.  Pour plus d’informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour masquer des contrôles lorsqu'une feuille de calcul est imprimée  
  
1.  Créez ou ouvrez un projet Excel dans Visual Studio et vérifiez que **Sheet1** est visible dans le concepteur.  Pour plus d'informations sur la création de projets, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  À partir de l'onglet **Contrôles communs** de la **Boîte à outils**, faites glisser un contrôle <xref:Microsoft.Office.Tools.Excel.Controls.Button> vers une cellule sur `Sheet1`.  
  
3.  Dans la fenêtre **Propriétés**, affectez à la propriété <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> la valeur **False**.  
  
## Voir aussi  
 [Contrôles sur des documents Office](../vsto/controls-on-office-documents.md)   
 [Vue d'ensemble des contrôles Windows Forms dans les documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Comment : ajouter des contrôles Windows Forms à des documents Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Comment : redimensionner des contrôles dans des cellules de feuille de calcul](../vsto/how-to-resize-controls-within-worksheet-cells.md)  
  
  